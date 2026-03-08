Algo que
no exame beta, mas que está aparecendo
bastante no exame final em 2025, é o Athena Federated Queries.
Portanto, prestem atenção, pessoal!
Não é mais o caso de Athena falar apenas com S3.
Por meio desses conectores de fontes de dados, você também
pode se comunicar com outras fontes.
Esses são apenas pequenos trechos de código executados no
Lambda que permitem que outras fontes de dados sejam compatíveis
com o Amazon Athena.
E há uma lista muito longa dessas fontes de dados
disponíveis.
Dentro do ecossistema do AWS, temos alguns para CloudWatch,
DynamoDB, DocumentDB, RDS e OpenSearch.
Além disso, qualquer banco de dados SQL que fale JDBC também é válido.
Há também um conector de fonte de dados para isso.
E, se houver algo realmente incomum, você
também pode escrever seu próprio conector personalizado
para conectar essa fonte de dados ao Athena.
Há também uma longa
lista de fontes de dados de terceiros.
Portanto, se você tiver dados hospedados
no Cloudera ou no Hortonworks, um banco de dados HBase,
Kafka e Oracle, Snowflake, Teradata
e muito mais.
Também há conectores de fontes de dados disponíveis
para esses casos.
Portanto, o Athena pode se conectar a praticamente qualquer coisa atualmente.
Um pouco mais de detalhes sobre isso.
O Athena também oferece suporte a exibições em fontes de dados federadas.
Agora, as informações para essas exibições são armazenadas
no AWS glue e não na própria fonte de dados subjacente.
Você também pode usar o AWS Secrets Manager para
gerenciar as credenciais dessas fontes de dados externas.
O único problema é que você precisa configurar
um endpoint privado de VPC para o AWS Secrets Manager for Athena
para poder usá-lo com sua
fonte de dados externa.
Além disso, por falar em cola,
alguns conectores podem ser integrados à própria cola da AWS.
Ao fazer isso, você pode habilitar o controle de acesso
refinado por meio da formação
de lagos, e alguns dos conectores
que suportam isso são os do Redshift, BigQuery, DynamoDB, snowflake
e MySQL, entre outros.
É curioso que as fontes
de dados compatíveis com o Google também estejam disponíveis lá.
Você também pode fazer consultas federadas entre contas.
Portanto, se você precisar fazer uma consulta em várias
contas, isso também é possível.
É apenas uma questão de configurar as permissões apropriadas
no IAM, e os detalhes não são importantes.
Você só precisa saber que pode fazer isso.
Além disso, há algo chamado Passthrough Queries (consultas de passagem).
Isso permite que você use a linguagem de consulta nativa
da fonte de dados que está sob os capuzes.
Portanto, se a sua fonte de dados subjacente tiver sua
própria linguagem de consulta,
você poderá passar essa consulta por baixo dela para que ela
tenha um desempenho um pouco mais eficiente e
tire proveito de todos os recursos que a fonte
de dados possa ter antes
de retornar esses dados ao Athena.
Um pequeno exemplo à direita aqui.
Portanto, essa é a aparência da sintaxe
do Query no CloudWatch por meio de um conector de dados.
Dê uma olhada na cláusula "De".
Aqui, você pode ver que ela se parece
muito com uma tabela, meu catálogo do CloudWatch, e temos
DOT e, entre aspas, algumas informações
extras que você pode precisar passar para essa fonte
de dados.
Portanto, neste caso, estamos
dizendo que queremos consultar os logs do CloudWatch
que estão nesse diretório específico.
Portanto, a sintaxe é bastante simples para fazer isso.
Além disso, lembre-se de que alguns conectores
também podem ser usados como fontes de dados Spark DSV2.
Não vou entrar em detalhes sobre isso,
mas, novamente, saiba que é uma possibilidade.
Portanto, alguns desses conectores de fonte de dados também podem ser
usados para fazer com que essas
fontes de dados se pareçam com as fontes de dados do Spark.
São as consultas da Athena Federated.
Basta lembrar que eles existem e o que podem fazer.
