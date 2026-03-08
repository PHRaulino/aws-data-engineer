outro recurso mais recente do Amazon S3.
E isso está se tornando uma espécie de
coração da oferta de dados da Amazon.
Portanto, eles estão desenvolvendo um
ecossistema de dados Lakehouse que é
construído em grande parte sobre as
tabelas S3 daqui para frente.
Portanto, essa parece ser a direção futura
da AWS no momento.
Eles também estão lançando algo
chamado SageMaker Lakehouse da Amazon.
E se você estiver assistindo a este vídeo
em 2026,
isso é muito novo para estar no exame
agora.
Portanto, não vou falar sobre isso com
muita profundidade, mas é basicamente o
conceito
que une essas três tabelas às outras
ferramentas de análise do ecossistema da
Amazon.
Em sua essência, é uma solução de data
lake gerenciada.
Portanto, é uma forma de armazenar muitos
e
muitos dados no S3 em formato tabular,
deixando
que o S3 se preocupe com todos os
detalhes do gerenciamento e da manutenção
desses dados
e com seu desempenho ao longo do tempo.
Assim como você pode criar um bucket de
uso geral no S3 para armazenar dados CSV
ou qualquer outra coisa, os Buckets de
tabela
são mais especializados em dados tabulares
e
armazenam dados especificamente no formato
Apache Iceberg.
Falaremos sobre isso daqui a pouco.
Portanto, no final das contas, você pode
simplesmente emitir consultas
SQL a partir de qualquer uma de suas
ferramentas favoritas.
Qualquer coisa que possa suportar o
Iceberg pode conversar com as tabelas S3.
Essa é a coisa mais legal. Espere, o que é
Iceberg?
Pode ser a primeira vez que você está
ouvindo esse termo.
Falaremos mais sobre isso quando falarmos
sobre o Amazon Athena e as
ferramentas de análise disponíveis no AWS.
Basicamente, porém, é um formato de tabela
padrão usado em grandes lagos de dados.
Ele foi projetado para dados em escala de
petabytes e
veio originalmente da Netflix. Eles também
têm muitos dados.
Ele oferece conformidade total com os
ativos, o que é bom,
e atualizações e exclusões em nível de
rolagem, o que pode
ser importante para fins de conformidade
em todo o mundo.
Ele também tem recursos para atualizar
suas tabelas à medida que
os dados evoluem, o que é chamado de
Schema Evolution.
Portanto, se você precisar alterar suas
colunas
ou os nomes das coisas, ele tem
maneiras de gerenciar isso sem quebrar
tudo.
Ele também possui alguns recursos
interessantes de particionamento.
Portanto, se você precisar alterar seus
esquemas de
particionamento, o Iceberg também facilita
um pouco isso.
Você também pode fazer consultas de dados
históricos,
fazer reversões com facilidade, observar
as alterações
entre as atualizações, gerenciamento
eficiente de metadados.
Falaremos mais sobre isso mais adiante no
curso.
Mas, para que você tenha uma visão
geral do que é o Iceberg.
E, mais uma vez, daqui para frente, a
SageMaker Lakehouse da Amazon é a marca
com
a qual eles vão embrulhar as mesas
Iceberg.
Você ouvirá mais sobre isso no futuro.
Mas o importante é que isso engloba coisas
como ferramentas de terceiros, incluindo
Spark, Flink, Trino,
Presto, Hive, todas elas podem falar
Iceberg, certo?
Portanto, todas elas têm integrações
nativas com o
formato Apache Iceberg e também têm
integrações com
os serviços do AWS Analytics e serviços de
dados, como AWS Glue, Redshift, EMR,
Athena e
alguns outros que veremos em um minuto.
Portanto, o Iceberg é basicamente a língua
franca de
dados para a qual todo o ecossistema da
Amazon e de terceiros está convergindo
para padronizar
a forma como esses dados tabulares são
armazenados.
E as tabelas S3 usam o Iceberg como
formato de armazenamento.
Então, mais uma vez, como as tabelas S3
são criadas
no formato Iceberg, isso as torna
compatíveis com muitas coisas.
Agora, nos bastidores, o catálogo de dados
Glue será o que conectará as tabelas
do S3 aos serviços analíticos do AWS.
Portanto, o que acontece é que, quando
você integra
tabelas S3 com os serviços analíticos da
AWS,
elas aparecem no catálogo de dados do
Glue,
tornando-as acessíveis a qualquer
ferramenta analítica da Amazon.
E, daqui para frente, eles poderão se
referir a ela como SageMaker Lakehouse.
E vou apenas dizer isso.
Novamente, isso não estará no exame em
2026, mas
acho que terá um papel importante nos anos
futuros.
Esses serviços incluem o Amazon Athena,
que
é usado para consultar dados na nuvem.
O Amazon Redshift, sua solução de data
warehouse,
o Amazon Quick Suite, que é a
nova marca do Amazon Quick Site, que
é basicamente a ferramenta para análise de
dados, gráficos, diagramas e tudo o mais.
O Amazon Elastic MapReduce também
apresenta
compatibilidade com tabelas Iceberg e
S3, Amazon SageMaker Unified Studio.
SageMaker mais do que apenas sua
plataforma de dados.
É também sua plataforma de aprendizado de
máquina.
E se você quiser emitir consultas SQL por
meio do SageMaker,
poderá fazer isso para tabelas S3 também
por meio do Iceberg.
Além disso, o AWS Glue ETL é outra maneira
de interagir com
os dados, e você também pode interagir com
as tabelas do S3.
Não é de se surpreender, pois, novamente,
ele está usando o catálogo Glue Data
para manter o controle desses dados.
Além disso, o Amazon Data Firehose,
anteriormente conhecido como Kinesis Data
Firehose.
Isso também pode ser integrado aos dados
da tabela S3 por meio do Iceberg.
E, por fim, há um ponto de extremidade
REST do Iceberg exposto também nas tabelas
S3.
Portanto, qualquer outra coisa que possa
se comunicar com os dados do Iceberg
por meio de uma interface REST também pode
se comunicar com as tabelas
do S3, incluindo o Spark, o Flink e muitas
outras ferramentas de terceiros.
E o Spark, a propósito, também tem a
capacidade de se comunicar
com as tabelas do S3 diretamente, sem esse
ponto de extremidade REST.
Portanto, há suporte nativo para tabelas
S3
incorporadas ao Spark que também está
disponível.
Portanto, é um padrão muito comum
armazenar dados
em tabelas do S3 e, em seguida, analisar
e manipular esses dados usando o Apache
Spark.
