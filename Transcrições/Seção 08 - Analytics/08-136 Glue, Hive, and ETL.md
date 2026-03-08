Hive, mas, basicamente, o Hive é um
serviço que você pode estar executando no
Elastic MapReduce e que permite emitir consultas do
tipo SQL em dados acessíveis ao cluster EMR.
Digo semelhante ao SQL porque, tecnicamente, ele se chama
HiveQL, mas as diferenças entre o HiveQL e o SQL não
são importantes para o propósito do exame.
O importante, porém, é que
você saiba que o Glue pode ser integrado ao Hive.
Portanto, você pode usar o catálogo de dados do AWS Glue que foi extraído
pelo rastreador do Glue como seu armazenamento de metadados para o Hive.
No Hive, isso é chamado de metastore.
Essa é uma espécie de terminologia especial da Hive.
Por outro lado, você também pode importar um metastore do Hive para o Glue.
Portanto, se você tiver um metastore Hive
ou um banco de dados Hive no EMR, também poderá
criar um Glue Data Catalog a partir desse
metastore Hive.
Você pode ir para os dois lados.
Isso fará um pouco mais de sentido quando falarmos
mais sobre o Hive e com mais profundidade mais
adiante, mas lembre-se de que o Glue Data Catalog pode
fornecer metainformações ao Hive em execução no EMR.
Assim como o Glue pode fornecer o Glue entre
seus dados não estruturados no S3 e os
serviços da Amazon, como Redshift e Athena.
Ele também pode fornecer
a cola entre os serviços em execução no cluster de EMR, ou seja,
aplicativos de código aberto mais tradicionais,
como o Apache Hive.
Vamos falar um pouco mais detalhadamente sobre o Glue ETL.
Novamente, isso é muito importante para o exame.
Não há muita coisa que você precise saber, mas você precisa saber.
Portanto, certifiquem-se de internalizar esse material, pessoal.
Portanto, o Glue ETL gerará automaticamente
ou poderá gerar automaticamente o código para você
transformar seus dados.
Portanto, você pode acessar o console da Amazon
e dizer como deseja transformar seus dados
de forma gráfica, e ele
gerará automaticamente um código para você
que será executado em Scala ou Python e aproveitará
o mecanismo do Apache Spark que está sendo
executado sob o capô do Glue ETL.
Portanto, você também pode escrever seu próprio código,
se quiser, usando Scala ou Python.
Ele lidará com a criptografia.
Portanto, você pode ter a criptografia do lado do servidor em repouso
ou a criptografia SSL para lidar com dados em trânsito.
Ambos são tratados para você.
O Glue ETL pode ser orientado por eventos.
Assim, você pode ter processos de ETL que são iniciados automaticamente
assim que novos dados são vistos pelo Glue.
Além disso, talvez você
precise provisionar uma DPU adicional, que é uma unidade
de processamento de dados para aumentar o desempenho dos trabalhos
subjacentes do Spark.
Portanto, mesmo que o Glue se construa como totalmente gerenciado, por baixo
do pano, ainda há servidores que precisam executar esses
trabalhos do Spark que estão
executando os processos de ETL para você.
E se achar que está demorando muito, você
pode provisionar DPUs adicionais para dar ao cluster
do Spark que está sendo executado sob o capô
um pouco mais de capacidade
para trabalhar.
Como você sabe de quantas DPUs precisa?
Bem, você pode ativar as métricas de trabalho em seu trabalho de ETL do Glue
para ajudar a entender a capacidade máxima de que você precisa.
Portanto, o processo para descobrir quantas DPUs você precisa
definir para o seu cluster é ativar as métricas do trabalho, estudá-las
e, em seguida, definir a capacidade máxima de DPUs em seu
trabalho com antecedência.
Esse é o processo que você segue para ajustar o desempenho
do trabalho de ETL do Glue.
Para ser mais específico, você visualizará
essas métricas no console do Glue, em vez de no CloudWatch,
e algumas coisas que você
pode plotar seriam o máximo de executores necessários
em comparação com o máximo de executores alocados
para ver se não há o suficiente para todos.
E uma vez que você tenha essas informações, poderá descobrir
quantas DPUs são necessárias para atender ao número
de executores que você realmente precisa.
Portanto, lembre-se de que uma DPU inclui dois executores,
mas você precisa reservar uma DPU para o driver do Spark e um executor
para a sobrecarga de gerenciamento.
Assim, levando isso em conta, você
pode chegar ao número apropriado
de DPU para um determinado trabalho.
Você também pode traçar a movimentação de dados ETL para garantir
que haja capacidade suficiente de movimentação
de dados.
Portanto, novamente, você pode traçar essas métricas no console
do Glue e usar essas informações para ajustar
o número de DPUs alocadas ao seu trabalho.
Se houver erros encontrados ao longo do pipeline do Glue ETL, você poderá
reportá-los automaticamente ao CloudWatch.
E se quiser ser notificado sobre isso,
você pode até mesmo vincular um CloudWatch ao SNS para
garantir que você seja notificado ou receba uma mensagem
de texto ou o que quer que seja se o seu processo de ETL tiver problemas.
Então, novamente, quero ter certeza de que você entendeu isso.
O Glue ETL é um sistema que permite processar e transformar automaticamente
seus dados.
Você pode fazer isso por meio de uma interface
gráfica que permite definir como
deseja que essa transformação funcione.
E, na verdade, ele fará isso usando
o Apache Spark, usando código Scala ou Python, totalmente
criptografado, tanto em repouso quanto
em trânsito.
Pode ser orientado por eventos, se você quiser, ou pode
ser executado em um cronograma.
Um pouco mais sobre o Glue ETL.
Então, mais uma vez, só quero reforçar isso.
Ele pode ser usado para transformar seus
dados, limpar seus dados ou enriquecê-los
antes de fazer a análise.
Ele gerará o código ETL em Python ou Scala e você poderá modificar
esse código, se necessário, depois que ele for
gerado.
Portanto, se o código gerado não estiver fazendo exatamente o que você deseja, você pode
simplesmente entrar e modificar esse código para ajustá-lo e fazer
exatamente o que deseja.
Portanto, você pode usar o código gerado automaticamente como uma espécie de
ponto de partida e construir em cima dele.
Essa é uma ótima
maneira de realizar operações mais complicadas usando o Glue ETL.
Você também pode fornecer seu próprio
código se quiser usar seus próprios scripts Spark ou pi Spark.
Portanto, um script do Spark pode estar pronto
em Scala, mas se você preferir Python, o que muitas pessoas no mundo
da análise de dados fazem, você
pode simplesmente fornecer um script Python
para o Spark chamado PySpark para o Glue ETL trabalhar, e ele simplesmente
o entregará ao mecanismo
subjacente do Apache Spark para transformar esses dados, limpá-los,
enriquecê-los, o que quer que você precise fazer para
processar esses dados antes de analisá-los de fato usando sistemas posteriores.
O destino do Glue ETL pode ser o S3 ou pode se comunicar por
meio de uma interface JDBC com algum outro
banco de dados, incluindo RDS ou Redshift, ou pode gerar
dados para o Glue Data Catalog.
Portanto, você poderia ter
um trabalho de ETL que apenas gerasse um catálogo de dados também.
Mais uma vez, ele é totalmente
gerenciado, embora você tenha
algum controle sobre os recursos
subjacentes, quantas DPUs você tem, como falamos, é
muito econômico.
E, novamente, com a maioria desses sistemas gerenciados sem servidor,
você só paga pelos recursos
que realmente pode consumir.
Os trabalhos são executados em uma plataforma Spark sem servidor,
e dizemos sem servidor porque, na verdade, há servidores
sob o capô executando o código Spark,
mas você não os vê nem precisa gerenciá-los.
É por isso que o chamamos de serverless.
É todo tipo de mágica.
Há um agendador do Glue que pode ser usado para agendar esses trabalhos
ou você pode usar os acionadores do Glue para executar
automaticamente os trabalhos com base nos eventos que desejar.
Portanto, reserve um momento
para internalizar este slide e as informações nele contidas.
Material muito importante para entender para o exame.
Então, como você faz para aplicar
essas transformações de ETL no Glue?
Bem, a principal estrutura de
dados com a qual você estará interagindo é chamada de quadro dinâmico.
E se você estiver familiarizado com o Apache
Spark, isso lhe parecerá muito familiar.
É muito parecido com um objeto de quadro de dados do Spark.
A única diferença é que ele tem mais material
de ETL disponível para você dentro dessa classe.
Ele tem APIs Scala e Python disponíveis, como você preferir.
E, da mesma forma que um quadro de dados,
é uma coleção de linhas e Spark.
Um quadro dinâmico é uma coleção de registros dinâmicos, em que os
registros dinâmicos são registros autodescritivos
que têm algum tipo de esquema associado a eles.
Portanto, neste diagrama à direita, você
pode pensar no quadro dinâmico
como abrangendo uma coleção de registros dinâmicos e cada
registro dinâmico contém campos, colunas, como queira
chamá-los dentro desse registro.
Nesse caso, ID, ano, mês, mas pode ser qualquer coisa, certo?
E você pode ter quantos registros dinâmicos quiser.
Todos eles serão armazenados de forma distribuída,
provavelmente no S3 sob o capô, certo?
Então, apenas para tornar isso real, aqui estão alguns trechos de código.
Lembre-se de que nunca será solicitado
que você escreva código no exame em si, mas se você for um programador, isso pode
ajudá-lo a tornar o exame mais concreto.
Por exemplo, se você quisesse criar um DynamicFrame chamado
pushdownEvents, poderíamos simplesmente dizer Glue context, obter a fonte
do catálogo e carregá-la de alguma tabela
do banco de dados em algum lugar.
E, em seguida, para aplicar um mapeamento a esse quadro dinâmico,
poderíamos simplesmente chamar pushdownEvents, apply mapping.
E o que isso fará é aplicar esse mapeamento
a cada registro dentro desse quadro dinâmico.
É claro, de forma distribuída.
Esse é o ponto principal, certo?
Portanto, em um exemplo específico, estamos definindo
um mapeamento que converte as IDs de strings para longs.
Ele está renomeando o campo de login do ator para apenas ator, o nome do repositório
para apenas repositório, e assim por diante.
Os detalhes não são muito importantes,
mas isso ajuda a entender o conceito aqui.
Você pode criar um quadro dinâmico.
E com apenas algumas linhas de código,
podemos aplicar um mapeamento complexo
a cada registro em nosso quadro dinâmico
de forma distribuída.
Vamos falar um pouco mais sobre as transformações
que você pode fazer com o Glue ETL.
Há certas transformações agrupadas que vêm com
ele imediatamente e que incluem campos suspensos
ou campos nulos.
Portanto, se você quiser apenas remover
dados vazios, o que é uma operação muito comum no pré-processamento.
Ele pode fazer isso para
você com apenas alguns cliques.
Assim, ele pode eliminar automaticamente campos ou eliminar campos
nulos para remover dados vazios dos dados de entrada para você.
Também é possível fazer filtros nos quais você especifica sua própria
função para filtrar registros.
Portanto, se você precisar especificar alguns critérios
para descartar valores discrepantes ou dados que possam não estar
dentro dos limites esperados, poderá configurar
esses filtros para filtrar os
registros com base nesses critérios.
Ou talvez você queira extrair apenas um subconjunto
de seus dados para análise.
Esse é outro uso válido dos filtros, certo?
Talvez você queira dizer que só quero filtrar
dados dos EUA para este trabalho, ou que só quero dados do Reino
Unido, o que quer que seja.
Uma transformação de filtro permitirá que você
faça isso, e essa é uma operação
agrupada que é muito fácil de fazer com o Glue ETL.
Você também pode fazer junções.
Essa também é uma transformação agrupada
que é fornecida como parte do Glue ETL.
Portanto, se você precisar enriquecer seus dados unindo-os
a outras tabelas, poderá fazer isso.
Uma operação comum é pegar
algum código, como
o código de um país ou algo assim, e enriquecê-lo
com o nome completo do país.
Quero dizer, não quero entrar muito na teoria do banco de dados,
mas as uniões são geralmente usadas para enriquecer os dados.
Por exemplo, eu uso muito o conjunto de dados de lentes de filmes em
meus cursos, nos quais você pode ter uma ID de filme.
Se você quiser realmente colocar o nome do
filme nos dados de saída, poderá
fazer uma junção com uma tabela separada
que mapeie IDs de filmes para nomes de filmes, por exemplo.
Você também pode fazer mapas.
E isso permite que você faça coisas como adicionar
campos aos seus dados, excluir campos
ou realizar pesquisas externas manualmente.
Portanto, se você só precisa transformar
os dados em uma linha de cada vez, talvez isso inclua apenas a
seleção dos campos que deseja passar para a análise
final.
Essa é uma operação muito comum.
Você pode usar uma operação de mapa para fazer isso.
Assim, por exemplo, se houver várias
colunas de dados chegando aos seus dados, você poderá usar
uma operação de mapa e o Glue ETL para extrair
os campos que realmente
lhe interessam e excluir os que não lhe interessam.
Há também transformações de aprendizado de máquina agrupadas,
o que é muito legal.
Uma que você provavelmente verá mencionada
no exame é a transformação encontrar correspondências de ML.
E seu objetivo é identificar registros duplicados ou correspondentes
no seu conjunto de dados, mesmo que esses registros não tenham um identificador
exclusivo comum e nenhum campo corresponda
exatamente.
Assim, ele pode realmente aprender como é um registro duplicado, mesmo
que não seja realmente uma duplicata.
Por exemplo, se você tiver endereços duplicados que variam,
sabe, por alguma coisa sutil, como
alguém soletrar a rua em vez de usar
a abreviação, poderá usar o find Matches
ML para lidar com isso.
Portanto, isso está disponível para você,
mas lembre-se de que ele existe e é isso que faz.
Você também pode usar o Glue ETL para conversões de formato.
E alguns formatos compatíveis que ele pode converter automaticamente
entre nossos valores separados por vírgula CSV.
JSON, Avro, Parquet, ORC e XML.
Portanto, muitas vezes, os dados chegam em um formato e você precisa
transformá-los em outro.
Para um sistema downstream, o Glue ETL pode fazer
isso para você com muita facilidade.
E também como, novamente, ele está usando o Apache
Spark como base, tudo o que o Apache Spark pode fazer, você
pode fazer com o Glue ETL.
Isso inclui até mesmo coisas sofisticadas, como o K-means
clustering, que vem do pacote Spark XML lib.
Falaremos mais sobre o Spark mais adiante no
curso, mas lembre-se de que tudo o que o Spark pode fazer, você pode fazer um ETL.
Mais uma vez, preste atenção a este
slide Guys, pois é importante
entender a fundo o Glue ETL e o que ele pode fazer.
Outro método do quadro dinâmico Glue sobre
o qual quero falar é a escolha de resolução.
Ouvi dizer que isso está aparecendo no exame
agora, então devemos falar sobre isso.
Seu objetivo na vida é lidar com as ambiguidades
em seu quadro dinâmico e retornar um novo quadro
que não tenha ambiguidades.
O que quero dizer com ambiguidade é que, por exemplo,
se eu tiver dois campos com o mesmo nome em meu quadro
de dados, isso seria uma ambiguidade que precisaríamos
resolver de alguma forma.
E há quatro maneiras de lidar com essas ambiguidades
neste momento.
Uma delas é que você poderia fazer chamadas de sublinhado como um parâmetro
para a API de escolha de resolução.
E o que isso fará é criar uma nova coluna
para cada tipo exclusivo em que esse nome aparece.
Portanto, veja este exemplo aqui na parte
inferior, onde temos um quadro dinâmico myList que
contém dois campos chamados price (preço).
Um deles é um número numérico de posição dupla.
A outra é uma cadeia de
caracteres que contém o símbolo do cifrão.
Portanto, se fizermos uma chamada de sublinhado
nesse exemplo, teremos duas novas colunas,
uma chamada price_double e outra
chamada price_string para resolver essa ambiguidade.
Outra opção é apenas cast,
o que forçará cada instância a ser convertida
em um tipo específico.
Também podemos dizer make underscore
struct, que cria uma estrutura dentro do seu registro que contém cada
tipo de dados individualmente dentro dessa
estrutura para o preço.
Portanto, podemos ter uma nova estrutura chamada preço.
Dentro dessa estrutura de preço, haveria a versão
decimal e a versão em cadeia desse nome de campo.
E, por fim, temos o projeto que projetará cada tipo
em um determinado tipo.
Assim, por exemplo, eu poderia dizer project:string, e
isso forçaria tudo a ser um tipo de dados de string.
Portanto, isso forçaria o 100. 00 tipo decimal para ser
uma cadeia de caracteres.
Portanto, é disso que se trata a escolha resolvida.
Trata-se apenas de resolver ambiguidades
em que você tem colunas diferentes
com o mesmo nome em seu quadro dinâmico.
