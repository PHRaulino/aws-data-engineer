O Redshift é a solução de data warehouse distribuído da AWS.
Portanto, é um data warehouse em escala de petabytes que está
espalhado por um cluster inteiro, mas é totalmente
gerenciado.
Portanto, você sabe, não pensa
em cuidar desse grupo.
Eles cuidam de toda a manutenção do servidor para você.
Como o mundo do Big Data geralmente envolve
o mundo dos data warehouses e o tratamento de
grandes conjuntos de dados, não é
de surpreender que o exame passe muito tempo falando
sobre o Amazon Redshift.
Portanto, vamos dedicar muito tempo a isso também.
É necessário aprofundar-se muito no Redshift.
Portanto, prestem atenção, pessoal.
Tudo isso é importante.
Em um nível elevado, o que é o Redshift?
Bem, ele é um serviço de data warehouse rápido e avançado,
totalmente gerenciado em escala de petabytes.
E a Amazon afirma que ele oferece um desempenho 10 vezes
melhor em comparação com outros data warehouses.
Portanto, além de ser extremamente dimensionável,
é super rápido e atinge essa velocidade usando aprendizado
de máquina.
Execução de consultas maciçamente paralelas, chamada de MPP, e uso de armazenamento
colunar, sobre o qual falamos anteriormente, e uso
de discos de alto desempenho também.
Lembre-se de que o Redshift é um data warehouse, portanto,
foi projetado especificamente
para o processamento analítico on-line, OLAP.
Ele serve para consultar seus
dados e obter insights a partir deles em
um ponto de vista analítico.
Ele não foi criado para OLTP.
Para OLTP, normalmente você desejaria um armazenamento mais baseado em linhas,
de modo que não estará atingindo o data warehouse do Redshift
com taxas de transação enormes, esperando respostas rápidas.
Ele foi criado como uma ferramenta
de análise, e é por isso que está na seção de análise aqui.
Eles também afirmam que, além de ser super rápido
e super dimensionável, ele também é super barato.
Eles afirmam que é o data warehouse
em nuvem mais econômico, e não há custo inicial para usar
o Redshift.
E isso contrasta fortemente com a construção
de um enorme data warehouse no local.
Posso lhe dizer isso em primeira mão.
Você paga à medida
que utiliza os recursos que está consumindo
e isso pode acabar sendo 1/10 do custo ou menos dos data warehouses
tradicionais armazenados no local.
Além disso, ele oferece recursos de consulta
rápida sobre dados estruturados usando clientes familiares baseados
em SQL e ferramentas de BI, usando apenas conexões ODBC e JDPC padrão.
Portanto, ele se parece com outro banco de dados
relacional para o mundo externo, e você pode conectar
qualquer ferramenta analítica ou de visualização que desejar ao Redshift sobre ele.
Também é facilmente dimensionável.
Você pode aumentar ou diminuir seu cluster facilmente
com apenas alguns cliques no AWS Management Console ou com uma
única chamada de API.
Portanto, se você precisar aumentar
ou diminuir a escala, isso é muito fácil de fazer.
Não será automático, mas pelo menos é fácil.
Ele também usa replicação para aumentar sua disponibilidade
e backups contínuos para aumentar a durabilidade dos dados, além de poder
se recuperar automaticamente de falhas de componentes
e nós.
Para o monitoramento, ele se integra ao CloudWatch
e, para as métricas de utilização de computação, utilização de armazenamento
e tráfego de leitura e gravação no cluster, todas
elas estão disponíveis gratuitamente no CloudWatch.
E você também pode adicionar métricas personalizadas definidas pelo
usuário que podem ser adicionadas usando a funcionalidade
de métricas personalizadas do CloudWatch.
Ele também fornece informações sobre
o desempenho de consultas e clusters usando o AWS Management Console.
E isso o ajuda a diagnosticar problemas de desempenho,
como qual usuário ou consulta está consumindo muitos recursos.
Alguns casos de uso listados para o Redshift
são a aceleração de todas as suas cargas
de trabalho de análise.
Portanto, se você deseja apenas que seu data warehouse seja mais rápido, talvez seja
melhor migrar para o Redshift.
Ele usa, como dissemos, MPP de aprendizado de máquina
e armazenamento de colunas em discos de alto desempenho
e cache de resultados para torná-lo super rápido.
Talvez você também queira
usar o Redshift porque deseja unificar seu
data warehouse e seu data lake.
Falaremos em breve sobre o Redshift Spectrum, que é uma
maneira de importar seus dados não estruturados no S3
como apenas outra tabela em seu data warehouse.
Assim, você pode fazer junções
e outras coisas nos dados estruturados
que foram importados para os próprios servidores Redshift, juntamente com
as informações do data lake que estão
armazenadas no S3 em algum lugar.
Isso é muito legal.
Talvez você queira apenas modernizar seu data warehouse
e torná-lo mais rápido, mais escalável
e mais fácil de gerenciar.
O Redshift é uma maneira potencialmente fácil de fazer isso.
Além disso, há alguns casos de uso mais específicos
que são apresentados no white paper do AWS Big Data.
Isso incluiria a análise de dados de vendas globais, o armazenamento
de dados históricos de negociações de ações, a
análise de impressões e cliques em anúncios, a agregação
de dados de jogos e a análise
de tendências sociais.
Todos esses são exemplos de coisas que você pode fazer com
o Redshift ou com qualquer data warehouse.
Vamos começar a nos aprofundar na arquitetura
do próprio Redshift.
Então, basicamente, temos clusters que
são o nível mais alto aqui e que abrangem
toda essa imagem.
Um cluster é o principal componente de infraestrutura
de um data warehouse do Amazon Redshift.
E um cluster é composto por um nó líder,
que você vê aqui, e um ou mais nós de computação.
Você pode conter de 1 a 128 nós de computação, dependendo
do tipo de nó.
Portanto, não é infinitamente dimensionável,
mas 128 nós podem armazenar uma grande quantidade de dados
e cada cluster pode conter um ou mais bancos de dados.
Agora, os dados do usuário serão armazenados
nos nós de computação.
O nó líder está apenas gerenciando a comunicação
com os programas clientes e toda a
comunicação com os nós de computação.
Portanto, é uma espécie de interface entre seus clientes
externos para o Redshift e os nós de computação sob o capô.
Ele recebe todas as consultas dos aplicativos clientes, analisa
as consultas e desenvolve planos de execução, que são um conjunto
ordenado de etapas para processar essas consultas.
Em seguida, ele coordena a execução paralela desses planos com
os nós de computação e também
agrega os resultados intermediários
desses nós.
Por fim, o nó líder retornará esses resultados
para os aplicativos clientes.
Vamos falar mais detalhadamente sobre os nós de computação.
Portanto, os nós de computação são responsáveis
pela execução das etapas especificadas nos planos de execução
que estão recebendo do nó líder e pela
transmissão de dados entre si para atender
a essas consultas.
Em seguida, ele envia esses resultados intermediários
de volta ao nó líder para agregação antes de serem
enviados de volta aos aplicativos clientes.
Agora, cada nó de computação tem sua própria memória de CPU dedicada
e armazenamento em disco anexado, que são determinados
pelo tipo de nó que você escolher.
Muito bem, dentro do nó de computação temos fatias de nó.
Assim, cada nó de computação é dividido em fatias e uma parte
da memória e do espaço em
disco dos nós será alocada para cada fatia, onde ela processa
uma parte da carga de trabalho
atribuída a esse nó.
O número de fatias por nó é determinado
pelo tamanho do nó do cluster.
Tudo bem, isso é muito profundo,
mas você realmente precisa conhecê-lo.
Portanto, um cluster consiste em um nó líder e muitos
nós de computação, um ou vários nós de computação, e esse nó de computação,
por sua vez, consiste em fatias de nós que processam partes dos dados
que estão sendo fornecidos a ele.
