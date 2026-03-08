Vamos falar sobre o modelo de custo da Glue.
Bem, geralmente não.
Basicamente, você é cobrado por segundo
por seus trabalhos de rastreamento e ETL.
Portanto, você é cobrado com base no tempo que os rastreadores do Glue
levam para extrair esses esquemas dos seus dados
e no tempo que os trabalhos de ETL levam para processar
e transformar esses dados usando o Apache Spark.
Para o armazenamento, o primeiro milhão de objetos armazenados
e acessados é gratuito para o Glue Data Catalog, ou seja, um subsídio
bastante generoso, mas você sabe que, para aplicativos
de Big Data, é possível consumir um milhão de objetos com
relativa rapidez.
Se estiver usando um endpoint de desenvolvimento
para realmente editar seus scripts ETL usando um notebook, eles
serão cobrados por minuto, portanto, certifique-se
de fechá-los quando terminar.
Para cada minuto que você estiver usando esse notebook
em um endpoint de desenvolvimento para o Glue, você será cobrado por cada
um desses minutos, portanto, o relógio está correndo
quando você estiver fazendo esse desenvolvimento,
não o deixe funcionando e saia para almoçar por uma semana,
certo?
Antipadrões de cola, para que você não deve usar a cola?
Não muito, na verdade.
Eles se esforçaram muito para
torná-lo o mais flexível e de uso geral possível.
A única coisa que eles dizem para você
evitar é tentar usar vários mecanismos de ETL, portanto, lembre-se
de que o Glue ETL é baseado no Apache Spark.
Se você realmente quiser usar outros mecanismos,
como Hive, Pig ou algo do gênero, use o Data Pipeline
ou talvez o EMR para processar esses dados.
Essa seria a melhor opção.
Embora o Apache Spark possa fazer praticamente
tudo o que você gostaria de fazer atualmente,
não consigo imaginar um caso em que você precisaria usar
o Hive, o Pig ou qualquer outra coisa em vez do Spark, a menos que você tenha algum
código ou sistema legado que precise
integrar.
O que costumava ser um antipadrão era o fluxo de dados
com o Glue ETL, mas isso não é mais verdade.
A partir de abril de 2020, o Glue ETL passou a oferecer suporte
a processos de ETL de streaming sem servidor.
Portanto, ele pode ser conectado ao Kinesis ou ao Kafka
para ingerir dados de streaming, transformá-los
e limpá-los em tempo real.
Isso é muito legal.
Em seguida, ele pode armazenar os resultados no S3 ou
em algum outro armazenamento de dados de sua escolha.
Como isso funciona?
Bem, ele usa o streaming estruturado do Apache
sob o Apache Spark.
Portanto, essa é uma adição não muito nova, mas relativamente nova,
ao Apache Spark, em que
o streaming estruturado permite o processamento
em tempo real de dados de streaming.
Nos bastidores, o Apache Spark tem esses elementos
chamados conjuntos de dados que ele usa para transformar
lotes de dados nos quais está trabalhando, mas, com o streaming
estruturado, você basicamente tem um conjunto de
dados que continua crescendo à medida que os dados de streaming
são adicionados a ele, e ele pode transformar esses
dados usando o mesmo tipo de código que você usaria para o processamento
em lote.
Portanto, se você tiver um script Spark no Glue ETL criado para processar
dados em lote, geralmente é muito fácil adaptá-lo
também para dados de streaming,
o que é um recurso interessante.
Falaremos mais detalhadamente sobre o Apache Spark
mais adiante, mas os dados de streaming agora estão bem com o Glue ETL,
o que é muito legal.
