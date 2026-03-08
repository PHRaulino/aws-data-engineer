Apache Spark, de passagem, no contexto das transformações de ETL
do Glue, que usa o Spark por baixo do
capô, e no contexto mais amplo do EMR, que
pode executar um aplicativo Spark hospedado
em seu cluster EMR.
Então, vamos nos aprofundar em como isso funciona.
Portanto, o Apache Spark é uma estrutura de processamento
distribuído de código aberto comumente usada
para cargas de trabalho de Big Data.
E, como você pode ver neste diagrama,
ele fica ao lado do MapReduce como uma espécie de substituto
para a parte de análise dessa pilha.
Portanto, graças ao YARN, podemos
trocar o MapReduce por algo melhor.
O MapReduce era excelente
há 10 anos, mas, atualmente, o Spark o supera em muito.
E isso se deve ao fato de o Spark ter cache na memória.
Ele realiza a maior parte de suas operações na memória,
em vez de acessar o disco ou atravessar a rede.
E ele também tem um otimizador de execução de consultas.
Assim, podemos analisar uma consulta SQL complicada
e otimizá-la para garantir
que você tenha esse gráfico acíclico direcionado realmente
ideal que executa a consulta
da maneira mais eficiente possível.
Portanto, não se limita ao paradigma map and reduce.
Ele pode realizar operações mais complexas com mais eficiência.
E, como resultado disso, ele pode
ser muito mais rápido do que o MapReduce.
Como resultado, você realmente vê o Spark sendo usado
atualmente e não tanto o MapReduce.
O Spark pode ser escrito usando Java, Scala, Python ou R.
Eu diria que Python e Scala são as opções mais populares.
A propósito, o próprio Spark é escrito em Scala.
E o bom do Spark é que você pode realmente
reutilizar seu código em diferentes
aplicativos.
Portanto, devido à sua arquitetura de software, todos
esses módulos diferentes têm
uma interface comum.
Portanto, é muito fácil pegar o mesmo trecho de código
e usá-lo para diferentes tipos de aplicativos,
o que economiza muito trabalho.
Você pode usá-lo para processamento
em lote, que é mais ou menos onde tudo começou.
Também é possível fazer consultas interativas com o Spark.
Ele expõe uma interface JDBC, se você quiser, para que
possa se conectar a ele e consultá-lo diretamente
usando o Spark SQL.
Ele tem recursos de análise em tempo real, recursos de aprendizado
de máquina por meio da biblioteca MLLib e também pode fazer
processamento de gráficos por meio do GraphX, e por processamento
de gráficos não queremos dizer tabelas e gráficos, mas sim
gráficos de informações, como uma rede
social, esse tipo de gráfico.
Ele também tem streaming do Spark e streaming estruturado,
o que nos permite processar dados em tempo
real à medida que são recebidos de um fluxo de
dados, e isso se integra ao EMR com o Kinesis ou o Kafka.
Agora, o Spark não foi feito para OLTP.
Ele não foi criado
para receber milhares de transações por
segundo de algum site
externo ou algo do gênero.
É uma questão de OLAP.
Ele foi criado para executar consultas de longa duração
que podem levar alguns segundos, minutos
ou até mais para serem concluídas.
Portanto, é realmente para análise de aplicativos
OLAP, não para OLTP.
Lembre-se disso.
Como isso funciona?
Bem, esta é a aparência da arquitetura do Spark.
Os aplicativos Spark são divididos em processos individuais
que são executados em seu cluster.
Portanto, no centro de tudo isso está um SparkContext
chamado seu programa de driver.
Esse programa de driver coordena todos esses outros processos
por meio do gerenciador de cluster,
que pode ser o próprio gerenciador de cluster integrado
do Spark ou, no caso do EMR ou de um cluster do Hadoop, o YARN, outro negociador
de recursos, o gerenciador de
cluster integrado ao Hadoop.
Mas você também pode executar um cluster autônomo
do Spark que não dependa disso.
E depois temos os executores que estão
fazendo todo o trabalho pesado.
Portanto, os executores executam todos os cálculos
e armazenam os dados associados ao seu trabalho.
E lembre-se de que, no EMR, isso pode estar sendo executado
em um nó central que tenha capacidade para HDFS ou em um nó de tarefa que não tenha.
O SparkContext é responsável por enviar
o código do aplicativo a esses executores e por enviar tarefas
individuais a esses executores para serem concluídas.
A faísca é composta de vários componentes.
Portanto, na raiz de tudo isso está o Spark Core.
Essa é a base da plataforma.
Ele é responsável pelo gerenciamento
de memória, recuperação de falhas,
agendamento, distribuição e monitoramento
de trabalhos, interação com o sistema
de armazenamento, que pode ser o HDFS, o EMRFS ou qualquer outro, e também oferece
suporte a todos os recursos necessários para se comunicar
com Java, Scala, Python ou nossos scripts.
Sob o capô desse nível baixo, ele
usa algo chamado conjunto
de dados distribuídos resilientes, ou RDD, mas provavelmente
não é necessário saber isso para o exame.
Além do Spark Core, há quatro sistemas principais,
um deles é o Spark SQL, que
evoluiu e se tornou
uma peça fundamental do Spark atualmente.
O Spark SQL é um mecanismo de consulta distribuída
que fornece consultas interativas de
baixa latência até 100 vezes mais rápidas do que o MapReduce.
Ele pode oferecer suporte a várias fontes
e formatos de dados, como JDBC, ODBC, JSON, HDFS, Orc, Parquet ou HiveQL, se você
for consultar tabelas do Hive.
Mas o mais importante sobre o Spark SQL é que
ele introduz o que é chamado de objeto de conjunto de dados
ou, no mundo do Python, um quadro de dados.
Basicamente, isso permite que você trate seus dados no Spark como
uma tabela de banco de dados gigante e
os consulte como se fossem uma.
Esse é realmente o poder do Spark SQL.
Ele nos fornece essa interface no estilo SQL para
nossos dados subjacentes no cluster EMR.
Também temos o Spark Streaming.
O Spark Streaming é uma solução em tempo real
que aproveita os recursos de agendamento rápido do Spark Core
para fazer análises de streaming.
Portanto, os dados costumavam ser ingeridos em mini lotes, mas, atualmente,
com o streaming estruturado, podemos fazer
streaming e processamento de dados
em tempo real usando conjuntos de dados.
E, mais uma vez, é muito legal que possamos usar o mesmo código
que escrevemos para o processamento
em lote e adaptá-lo ao streaming com muita facilidade
usando a arquitetura do Spark.
Ele aumenta sua produtividade
porque você pode reutilizar esse código
com muita facilidade e oferece suporte a dados de fontes como
Kafka, Flume ou HDFS e ZeroMQ.
Ele costumava ter suporte integrado ao Twitter,
mas atualmente isso é mais um complemento.
Eles meio que descontinuaram isso.
MLLib, um recurso muito importante.
Trata-se de uma biblioteca de algoritmos
para realizar aprendizado de máquina em dados em grande escala.
Assim, eles descobriram uma maneira de distribuir o processamento
de vários algoritmos populares de aprendizado de máquina.
Praticamente todos os que
você precisaria usar na prática
estão disponíveis para você, o que é realmente incrível.
Regressão, clustering, classificação,
filtragem colaborativa, mineração de
padrões, ele pode fazer
tudo isso e pode ler de qualquer fonte de dados que o
Spark possa ler, HDFS,
HBase ou qualquer coisa com a qual o Hadoop possa se comunicar.
Assim como o próprio Spark,
você pode escrever seus aplicativos
MLLib usando Scala, Java, Python ou R, mas é muito legal que finalmente tenhamos
uma maneira de fazer algoritmos complexos de
aprendizado de máquina em conjuntos de dados maciços,
sem estarmos limitados pela capacidade de
uma única máquina.
Eles decifraram o código
de como distribuir esse processamento.
Por fim, temos o GraphX.
Novamente, essa é uma estrutura de processamento de gráficos
distribuídos criada com base no Spark.
Ele oferece ETL, análise exploratória e computação
iterativa de gráficos para permitir que você crie e transforme
interativamente estruturas
de dados de gráficos em grande escala.
Ele é muito flexível, mas, sinceramente, não é muito usado.
Ultimamente, o Spark está em desuso e, portanto, não é provável
que você veja muito sobre
o GraphX em qualquer lugar.
Atualmente, ele foi suplantado por soluções de terceiros
em sua maior parte.
Vamos falar um pouco mais sobre o Spark
Streaming e o streaming estruturado
em particular, porque essa é uma parte muito interessante
e amplamente usada do Spark atualmente.
Portanto, os aplicativos Spark
geralmente usam o que chamamos de conjunto de dados em seu código.
E um conjunto de dados é basicamente uma tabela gigante de dados.
Portanto, você pode simplesmente tratar os dados no cluster
como uma tabela de banco de dados gigante.
E temos esse tipo de tendência
no mundo da análise de dados
em que o SQL se tornou uma espécie de língua franca de todos
esses sistemas,
de modo que praticamente tudo fala SQL atualmente.
e com o streaming estruturado, esse ainda é o caso.
Basicamente, você pode tratar seus
dados como uma tabela ilimitada em que novas
linhas são adicionadas o tempo todo a partir do
fluxo de dados.
Portanto, é simples assim.
Você o consulta da mesma forma
que consultaria um conjunto de dados de processo em lote, mas, com o streaming
estruturado, ele continua
crescendo com o tempo.
Agora, há alguns recursos extras adicionados a
ele para permitir que você selecione essas consultas,
portanto, se quiser restringi-las,
por exemplo, à última hora ou o que quer que seja, você pode fazer isso.
Você sabe que, neste exemplo,
estamos lendo um fluxo de dados JSON do S3 no diretório
de logs.
Estamos agrupando-os pelo campo de ação e estamos
estabelecendo uma janela na última hora e contando-os
neste exemplo.
Em seguida, enviamos esse resultado por meio da interface JDBC para algum banco
de dados MySQL em algum lugar.
Assim, você pode ter uma ideia do poder
do streaming estruturado aqui.
Com apenas essas duas linhas de código,
dissemos para monitorar os logs que
chegam a esse bucket S3 no formato JSON, adicioná-los
ao longo da última hora e gravar
os resultados a cada hora por meio de JDBC
em um banco de dados MySQL externo.
Não é legal?
Essa é uma operação muito complicada com
apenas duas linhas de código.
