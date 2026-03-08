Cara, parece que isso foi há muito tempo.
Falamos sobre o rastreamento da linhagem.
Portanto, o SageMaker tem um recurso chamado rastreamento de linhagem
do SageMaker ml que automatiza muito disso para você.
Assim, criaremos e armazenaremos automaticamente
seus fluxos de trabalho de aprendizado de máquina.
De forma mais ampla, chamamos isso de ML ops.
O campo de controle de todos os pipelines e processos
que entram em um fluxo de trabalho de aprendizado de máquina.
Ele manterá automaticamente um histórico de execução de seus
modelos e os rastreará para fins de auditoria e conformidade.
Ele pode rastrear automaticamente essas coisas para
você ou, se você quiser fazer com que as coisas façam
parte do rastreamento da linhagem manualmente,
também poderá criar entidades de rastreamento manualmente.
E se você precisar rastrear linhagens em diferentes
contas, poderá fazer isso também.
Você pode usar o AWS Resource Access Manager para
rastrear a linhagem entre contas.
Então, vamos dar uma olhada em um exemplo de
como pode ser um gráfico de linhagem do rastreamento
de linhagem do SageMaker ML.
Apenas para tornar isso real. Portanto, você pode ver aqui que temos
vários dados chegando.
Temos um artefato de conjunto
de dados e alguns artefatos de conjunto de dados chegando, bem como
um artefato de entrada de fluxo.
Portanto, algo que está sendo transmitido vai para o que chamamos
de componente de avaliação de trabalho de processamento.
E isso vai alimentá-lo em algum tipo de trabalho de treinamento.
Esse trabalho de treinamento é composto por uma série de coisas aqui.
O artefato do conjunto de
dados em si, ou seja, os dados do processo que chegam, dados de entrada adicionais, talvez
a especificação do algoritmo que queremos
executar nele e talvez uma imagem que contenha o código para essa
operação específica.
Uma vez concluído o treinamento,
isso pode criar um artefato de modelo, um artefato de ponto de verificação
e um artefato de configuração de dados de saída, talvez.
E esses artefatos de modelo podem
ser alimentados em um endpoint.
Esse endpoint pode então ser usado para alimentar os resultados
desse modelo para o mundo externo,
resultando em um contexto de endpoint.
E talvez haja um artefato de imagem ao longo do caminho,
onde foi criado um instantâneo do código para o próprio modelo
que está sendo hospedado.
Portanto, há várias entidades que ele pode rastrear.
Um deles é chamado de componente de teste.
Um exemplo de um componente de teste pode ser um trabalho de processamento,
um trabalho de treinamento ou um trabalho de transformação.
Podemos montar os componentes da avaliação em uma avaliação.
Portanto, esse é um modelo composto de componentes de teste.
Além disso, podemos agrupar testes para um determinado
caso de uso e chamar isso de experimento.
Também podemos ter contexto, que são apenas agrupamentos lógicos
de quaisquer entidades que logicamente fazem sentido juntas.
Há ações como parte de sua linhagem que incluem
etapas de fluxo de trabalho ou
implantação de um modelo, coisas desse tipo.
Os artefatos são gerados ao longo do caminho.
Podem ser objetos ou dados, como um
bucket S3 ou talvez uma imagem ECR.
E também podemos especificar associações entre entidades.
E, se quiser, você pode marcá-los com tipos de associação,
como contribuído para associado com derivado
de produzido.
Ou o mais legal é que você pode consultar essas coisas depois de
ter as linhagens.
Portanto, há algo chamado consulta de linhagem, API
que você pode acessar a partir do Python, que faz
parte do Amazon SageMaker, SDK para Python.
E, com isso, você pode fazer coisas como encontrar todos os modelos
ou pontos de extremidade ou -: o que
quer que seja que use um determinado artefato.
Então, se eu quiser descobrir, bem, se eu mover esse artefato ou
mudar alguma coisa nele, qual será o efeito disso?
Essa é uma maneira muito boa de
descobrir, usando o rastreamento de linhagem,
quais são essas dependências.
Ele também pode produzir visualizações bonitas,
como a que vimos no slide anterior,
que requer uma classe auxiliar de visualizador externo que
a AWS apenas disponibiliza no GitHub em algum lugar.
E é fácil de encontrar, mas não
está realmente incorporado ao rastreamento da linhagem em si.
Mas eles indicam o código para fazer isso.
