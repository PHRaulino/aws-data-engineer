Vamos falar um pouco sobre o Kinesis Data
Managed Service for Apache Flink.
É apenas uma forma de consultar fluxos de dados
e processar esses fluxos ao longo do caminho.
Então, historicamente, temos algo chamado
Amazon Kinesis Data Analytics, que ingeria dados do Kinesis Data
Streams ou do Kinesis Data Firehose, realizava algum tipo de
transformação neles à medida que o fluxo era
recebido e, em seguida, alimentava
os dados transformados em algumas ferramentas de análise ou em algum
destino downstream, certo?
Portanto, é basicamente uma maneira de fazer ETL de fluxo contínuo.
Hoje em dia, tudo o que resta dele se chama Kinesis
Data Analytics for SQL Applications, e isso nos
permite aplicar operações SQL a esse fluxo
à medida que ele passa.
E eu não ficaria surpreso
se isso fosse descontinuado muito
em breve, por isso não sei se esperaria ver isso no exame, pois acho
que está em suas últimas pernas, mas
a forma como funcionava conceitualmente era a seguinte: você poderia
ter dados provenientes de um fluxo de dados
ou de um firehose de dados e também poderia
ter o que é chamado de tabelas de referência hospedadas
no S3, que é uma forma de fazer uma junção realmente barata.
Mas, de qualquer forma, você pode aplicar essas transformações
SQL do Kinesis Data Analytics for SQL nesse fluxo de entrada, portanto,
basta fornecer um comando SQL e ele aplicará
isso à medida que os dados forem recebidos e os cuspirá
de volta nos fluxos de saída e também em um fluxo
de erro, se você quiser.
Esse fluxo de saída, que pode ser o Kinesis Data
Streams ou nosso firehose de dados,
pode então ser armazenado no Amazon S3
ou consultado por algo como o Amazon Redshift.
Agora, essa questão da tabela
de referência é importante.
É basicamente uma maneira de fazer pesquisas rápidas, certo?
Então, por exemplo, digamos que eu queira procurar a
cidade associada a um código postal,
posso ter esse mapeamento armazenado no S3,
que é uma maneira muito simples e econômica
de fornecer esses dados à minha consulta SQL.
Eu usaria apenas um comando de junção dentro
dessa consulta para fazer referência à tabela de referência
externa que está no S3.
Assim, também podemos emparelhar o Kinesis Data Analytics
com as funções Lambda. Ele não precisa apenas ir diretamente
para um fluxo, você também pode enviá-lo para o Lambda, o que lhe dá
ainda mais flexibilidade para o pós-processamento.
Posso agregar linhas, traduzi-las
para outro formato, transformar os dados
ainda mais e enriquecê-los, posso até mesmo criptografá-los,
se quiser, e também posso conversar
com outros serviços e outros destinos, o que me permite não apenas
conversar com coisas como S3 e Redshift, mas também
com DynamoDB, Aurora, SNS, SQS, CloudWatch, qualquer coisa com a qual o Lambda
possa conversar, ou seja, praticamente tudo.
Atualmente, no entanto,
o que está em alta é o Managed Service
para o Apache Flink, que tem uma longa história com a AWS.
Originalmente, ele se chamava Kinesis Data Analytics for Java,
depois foi renomeado para Kinesis Data
Analytics for Apache Flink, que é o nome atual.
No entanto, por baixo do capô, o Kinesis Data
Analytics sempre usou o Apache Flink,
então eles estão sendo mais transparentes com o que
estão fazendo e, em vez de apresentá-lo como uma espécie
de ferramenta exclusiva, estão dizendo:
"Bem, o que estamos oferecendo a você é apenas um ambiente gerenciado
para uma ferramenta de código aberto integrada ao AWS", que é a tendência
do AWS atualmente.
E não está mais restrito ao
Java, agora também suporta Python e Scala.
A propósito, o Flink é apenas
uma estrutura para processar
fluxos de dados, e é por isso que ele sempre foi
a tecnologia subjacente
do Kinesis Data Analytics.
Assim, o Managed Service for Apache Flink
integra o Flink ao AWS, portanto, em vez de usar
SQL, como vimos anteriormente, você pode desenvolver
todo o seu...
Seu próprio aplicativo Flink inteiro do zero e
carregá-lo no Managed Service for Apache Flink a partir do S3.
Basicamente, você desenvolve um
aplicativo Flink que faz o que quiser com
seus dados de streaming, carrega esse aplicativo
no S3 e, em seguida, diz: "Ei, Managed
Service for Apache Flink, aqui
está meu aplicativo Flink no S3, carregue-o
e hospede-o para mim. E, além da API DataStream para lidar com dados de
streaming, há também uma API Table
para acesso a SQL. Por
isso, acho que a análise de dados para SQL provavelmente
está indo embora, porque você pode fazer a mesma coisa com
o Apache Flink usando essa API Table em
vez da API DataStream.
Qual é o aspecto conceitual disso?
Sim, ele é sem servidor, obviamente, porque
é gerenciado, certo?
Isso não é preciso dizer.
Portanto, temos o que chamamos de Flink Sources
e, no contexto do AWS, isso pode
ser um fluxo de dados do Kinesis entrando, ou pode
ser o Amazon Managed Streaming for Apache Kafka entrando também,
se você tiver o Kafka entrando como uma fonte.
Isso é canalizado para o Managed Service for Apache Flink,
onde nosso aplicativo Flink real está fazendo algo,
nesse caso, usando a API DataStream
para operar no Kinesis ou no MSK e, novamente, esse aplicativo
real é carregado por meio do S3.
Depois que seu aplicativo faz o que precisa
fazer, ele pode continuar e conversar com outros
serviços da Amazon, que são Flink Sinks, que podem ser S3,
Kinesis Data Streams ou Kinesis Data Firehose para
gerar esses dados de streaming transformados.
Vamos falar um pouco mais amplamente
sobre o Apache Flink e como ele funciona, pois o exame
pode esperar que você se aprofunde
um pouco mais nesse assunto.
Portanto, em um nível mais alto, eles têm coisas chamadas
conectores dentro do Flink, e essas são
apenas maneiras de, bem, fazer o que ele diz, ou
seja, conectar o Flink a várias fontes de dados e a lugares
para onde você deseja enviar fluxos de dados.
From Java, you can create a connector
from the "flink-connector-kinesis"
library, that's a handy resource for
you, and that comes with a library of Table API
connectors that are included
as part of Flink, so that includes ways of easily
connecting the data sources from Kafka, DynamoDB, Firehose, Kinesis, MongoDB, Opensearch,
and anything that talks to JDBC,
along with a bunch of more obscure sources
as well, but mostly, they make it easy for
you, and as for connecting to other sources, there's also a custom "sink" connector you can write, so as long as you have an
SDK for it, you can still connect Flink to it, even if it's not
built into the Table API connectors, so for example, over on the AWS
blog, they have this example they wrote up of using Flink within this application
that puts stuff into Amazon Timestream from a Kinesis data-stream, and you can see Flink in kind of the top of the middle
there of this workflow, so what's going on there is that they have a connector that they're using from Java, from th
Agora, como ele faz essa transformação?
Bem, o...
O Flink também vem com vários operadores
que você pode usar em seu código
para transformar um ou mais fluxos de dados em um
novo fluxo de dados, e os operadores
que ele oferece são bastante semelhantes
aos do Apache Spark ou do MapReduce, de modo que eles
têm maneiras de mapear um conjunto de dados para outro, fazer um
"flatMap", filtrar dados à medida que eles passam, reduzir dados
com base em alguma chave, fazer janelas deslizantes
para fluxos e fazer operações conjuntas à medida que os dados do fluxo
passam.
Há também operadores para particionamento
físico, dividindo a forma como os
dados são armazenados, e também para encadeamento
de tarefas, se você quiser encadear diferentes
operações.
Alguns casos de uso comuns, streaming ETL, já
falamos sobre isso, se você quiser
fazer essa extração, transformação e
carregamento em tempo real à medida que os dados são recebidos, um aplicativo
Flink pode fazer isso para você.
Você também pode usá-lo para geração contínua de
métricas, portanto, se eu quiser monitorar
um fluxo de dados e manter um registro em tempo real de como as coisas estão indo,
essa pode ser outra aplicação.
Análise responsiva, mais ou menos a mesma ideia, portanto,
se eu quiser uma análise em tempo real de quem
está acessando meu site ou qualquer outra coisa, essa
pode ser uma forma de implementar isso também.
