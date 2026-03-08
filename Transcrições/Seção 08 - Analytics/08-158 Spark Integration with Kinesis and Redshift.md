Vamos falar sobre o Spark streaming
com um pouco mais de profundidade.
Portanto, os aplicativos Spark, como dissemos, geralmente
usam algo chamado conjunto de dados em seu código para se referir
aos seus dados.
E um conjunto de dados é tratado de forma muito semelhante a uma tabela de banco de dados.
Com o streaming do Spark, e com o streaming
estruturado em particular, você pode
basicamente imaginar seus dados de streaming
como uma tabela de banco de dados que continua crescendo para sempre.
Assim, à medida que novos dados são recebidos
pelo fluxo, ele continua adicionando mais e mais
linhas a essa tabela de banco de dados virtual na forma de um conjunto de dados.
Portanto, você pode consultar esses dados usando janelas de tempo.
E se observarmos este exemplo, o que
este código está fazendo é dizer: vamos
monitorar todas as coisas que estão sendo lançadas
em um bucket de registros no S3.
E essa ação com uma janela de uma hora ao longo do tempo
significa que contaremos
continuamente os registros recebidos nesse intervalo
durante a hora anterior.
Em seguida, vamos escrever
essas contagens usando JDBC em um banco de dados MySQL externo.
Portanto, a quantidade de código que você precisa escrever
para algo como isso é, na verdade, bastante trivial.
E esse é o poder do Spark streaming e do
streaming estruturado em particular.
Sim, você precisa escrever
código, mas, em geral, é um código muito
simples, e você pode contar com o Spark para gerenciar todo o trabalho sujo de garantir
que você esteja obtendo seus dados de fluxo
de forma confiável e distribuindo o processamento desse fluxo em todo o
cluster de forma confiável.
Você se concentra apenas na lógica do que
deseja fazer, enquanto o Spark streaming cuida de todas as partes desagradáveis
para garantir que isso aconteça de maneira confiável.
Você também pode integrar o Spark streaming com o Amazon Kinesis.
E quero dizer que não há nada realmente mágico
na integração do Spark streaming com qualquer outro sistema, porque
é tudo código, certo?
E com o código, você pode fazer qualquer coisa.
Então, parece que alguém escreveu
uma biblioteca para streaming do Spark construída
sobre a biblioteca do cliente Kinesis para
permitir que o streaming do Spark importe dados dos fluxos de
dados do Amazon Kinesis.
E você só precisa conectar essa
biblioteca e codificar com ela.
E você pode tratar o Kinesis como qualquer outro fluxo de dados
que entra em um conjunto de dados no fluxo estruturado do Spark.
Assim, por exemplo, você pode ter alguns produtores
do Kinesis, digamos, um grupo de hosts EC2 gerando logs que
estão bombeando dados para um fluxo de dados do Kinesis.
Em seguida, você pode integrá-lo
usando o código de integração de conjunto
de dados do Spark, como qualquer outro conjunto de dados que chega
ao Spark Streaming, e processá-lo em todo o cluster
no EMR usando o Apache Spark.
Você também pode integrar o Spark ao Redshift.
Ainda não falamos sobre
o Redshift, mas, basicamente, ele é um enorme data warehouse
distribuído oferecido pela AWS.
E, assim como há um pacote Spark Kinesis, há também um
pacote Spark Redshift, que permite que
o Spark trate os conjuntos de dados do Redshift como qualquer
outro banco de dados SQL.
Portanto, isso faz com que o
Redshift se pareça com qualquer outra fonte de dados SQL para o Apache Spark.
E, novamente, você pode usar o poder do Apache
Spark em todo o seu cluster de EMR
para transformar e processar esses dados da maneira que desejar,
de forma altamente distribuída e escalonável.
Portanto, essa é uma boa maneira de fazer ETL no Redshift
usando o Apache Spark, por exemplo.
Imagine, por exemplo,
que temos um monte de dados de voos de companhias aéreas residindo
em um enorme lago de dados armazenado no Amazon S3.
Eu poderia, por exemplo, implantar o Amazon Redshift
Spectrum sobre esses dados no S3, que me
fornecerá uma interface SQL sobre esses
dados que estão no S3.
Agora, usando o pacote Spark Redshift, posso
criar um cluster do Apache Spark no Amazon EMR e usá-lo
para executar ETL nos dados que estão residindo
no S3 por meio do Amazon Redshift, porque o Redshift se parece
com qualquer outra fonte de dados SQL para
o Apache Spark.
Assim, ao integrar o Redshift com o Spark,
posso distribuir o processamento
desse enorme conjunto de dados armazenado
no S3 e, talvez, voltar e colocar esses dados processados
em outra tabela do Amazon Redshift para
processamento adicional.
Talvez eu esteja fazendo algo como preparar
esses dados para algum algoritmo
de aprendizado de máquina que
será usado no futuro, e esse algoritmo de
aprendizado de máquina pode usar esses dados preparados
e transformados na nova tabela do Redshift
que produzi com meu trabalho do Spark.
