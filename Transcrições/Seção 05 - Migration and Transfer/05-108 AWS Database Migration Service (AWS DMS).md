banco de dados dos seus sistemas locais para a nuvem do AWS.
Nesse caso, você deve usar o DMS,
ou Database Migration Service.
É um serviço de banco de dados rápido e seguro que permite
que você migre seu banco de dados
do local para o AWS, mas o mais legal é que ele
é resiliente e autorrecuperável.
E durante toda a migração, o banco
de dados de origem continua disponível.
E ele oferece suporte a vários tipos de mecanismos,
como migração homogênea, portanto,
de Oracle para Oracle ou Postgres para Postgres, mas também migrações
heterogêneas.
Por exemplo, se você
quiser migrar do Microsoft SQL Server para o Aurora e
ele for compatível com a replicação contínua de dados usando
o CDC, que é o Change Data Capture.
Por fim, para usar o DMS, você precisa
criar uma instância do EC2, e essa instância do EC2 executará
as tarefas de replicação para você.
Portanto, de forma muito simples, seu banco de dados de origem
pode estar no local e, em seguida, você
está executando uma instância do EC2
que tem o software DMS e ele extrairá dados do banco
de dados de origem, continuamente, e os colocará no banco de dados de destino.
Portanto, a pergunta
é: quais são as fontes e quais são os alvos?
Você não precisa se lembrar de todos
eles, mas dos mais importantes,
apenas para entender os conceitos por trás do DMS.
Portanto, as fontes podem ser bancos de
dados locais ou baseados
em instâncias do EC2, como Oracle, Microsoft SQL Server,
MySQL, MariaDB, PostgreSQL, MongoDB, SAP e DB2.
Também podem ser bancos de dados do Azure, como o Banco de Dados SQL do Azure.
Pode ser o Amazon RDS, qualquer banco de dados, inclusive o Aurora.
Pode ser o Amazon S3 e o DocumentDB.
Em termos de metas, bem, também
temos diferentes opções.
Temos bancos de dados no local e em instâncias do EC2.
Portanto, podemos ter Oracle, Microsoft SQL Server,
MySQL, MariaDB, PostgreSQL, SAP.
Também podemos ter qualquer banco de dados no Amazon RDS.
Podemos ter o Redshift, o DynamoDB, o Amazon
S3, o serviço OpenSource, o Kinesis Data Streams,
o Apache Kafka, o DocumentDB e o Amazon Neptune, bem
como o Redis e o Babelfish.
Portanto, você não precisa se lembrar
de tudo isso, é claro, mas a ideia geral é que o
DMS pode ajudá-lo a pegar um banco de dados, por exemplo,
um banco de dados local e colocá-lo, exportá-lo e migrá-lo para um destino que
é, praticamente, qualquer banco de dados que a AWS oferece.
Se você entender
isso, terá a ideia geral por trás do DMS.
E se o banco de dados de origem e o banco de dados de destino
não tiverem o mesmo mecanismo?
Em seguida, você precisará usar algo chamado AWS SCT, sigla em inglês para
Ferramenta de Conversão de Esquema, que converterá
o esquema do banco de dados de um mecanismo
para outro.
Assim, por exemplo, se você estiver usando um OLTP,
podemos migrar do SQL Server ou Oracle para MySQL, PostgreSQL ou Aurora.
Como você pode ver no lado esquerdo, o mecanismo de banco de dados
é diferente do que está no lado direito,
mas você também pode transformar para o processo
de análise, como Teradata ou Oracle, até o Amazon Redshift.
Portanto, a ideia é que aqui o banco de dados de origem tenha
um mecanismo diferente do banco de dados de destino.
No meio, temos o DMS, mas agora
ele também está executando o SCT, ou Schema Conversion Tool.
E o que você deve saber ao fazer o exame
é que não é necessário usar o SCT se estiver migrando o mesmo
mecanismo de banco de dados.
Portanto, se você estiver usando o PostgreSQL local para o PostgreSQL RDS,
é o mesmo agente de banco de dados, é o PostgreSQL.
Portanto, nesse caso, você não usará o SCT.
Mas se estiver fazendo algo como a conversão de Oracle para
Postgres, precisará usar o SCT.
Então, para que você saiba, o agente de banco de dados é o PostgreSQL,
mas o RDS é apenas uma plataforma que estamos
usando para executar esse mecanismo de banco de dados.
Então, como você configuraria
uma replicação contínua para o DMS?
Bem, você teria seu data center
corporativo, por exemplo, com um banco de dados Oracle
como origem e um banco de dados Amazon RDS para MySQL DB como destino.
E, como podemos ver,
temos dois tipos diferentes de banco de dados.
Portanto, nesse caso, precisamos usar o SCT, caso contrário,
ele não funcionará.
Portanto, a Schema Conversion Tool.
Portanto, configuramos um servidor com o AWS SCT instalado
e podemos configurá-lo no
local, essa é a melhor prática,
e depois faremos a conversão do esquema
em nosso banco de dados Amazon RDS executando o MySQL.
Em seguida, podemos configurar uma instância de replicação
do DMS que fará a carga total e a captura de dados de alteração, CDC, para ter
uma replicação contínua.
Assim, ele executará a migração
de dados lendo o banco de dados local,
o banco de dados Oracle de origem, e inserindo
os dados em suas sub-redes privadas.
É isso aí. Portanto, isso é tudo o que você precisa saber sobre o DMS.
Isso se refere ao Database Migration Service.
Lembre-se de que você precisa usar o SCT sempre que tiver dois
tipos diferentes de bancos de dados dos quais está migrando.
E para o DMS, há uma implantação de várias AZs.
Portanto, quando isso
acontece, você tem uma instância de replicação do DMS em uma AZ
e, em seguida, tem uma replicação síncrona
dessa instância em outra AZ, que será uma réplica em espera.
Portanto, a vantagem de usar isso
é, obviamente, ser resiliente a uma falha em uma AZ específica, mas
também oferece redundância de
dados, eliminará congelamentos de IO e minimizará picos de latência.
Então é isso para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
