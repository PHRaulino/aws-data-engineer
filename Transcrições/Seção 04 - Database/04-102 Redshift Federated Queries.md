Essa é uma maneira
de consultar e analisar bancos de dados, armazéns
e até mesmo lagos de dados.
Agora, vamos falar especificamente
sobre o caso de vincular o Redshift a outros bancos de dados,
com bancos de dados RDS em particular.
Portanto, o que podemos fazer é vincular o Redshift ao
Amazon RDS ou ao Aurora para PostgreSQL e MySQL atualmente.
Talvez isso se expanda no futuro.
Mas isso é interessante porque significa que posso acessar
dados em tempo real do RDS e consultá-los no Redshift.
Portanto, isso evita a necessidade de ETL, certo?
Não preciso me preocupar com a importação de dados
desses bancos de dados relacionais do Aurora ou
do RDS para o Redshift, posso simplesmente consultar
esses bancos de dados diretamente no local e evitar a necessidade
de mover esses dados.
Assim, isso me permite criar uma consulta no Redshift que atinge
tabelas que estão
em bancos de dados relacionais externos, como PostgreSQL
e MySQL, que estão no RDS.
Isso é muito legal.
Ele também transfere a computação para
esses bancos de dados remotos.
Portanto, isso também reduz ainda mais a movimentação de dados.
Isso significa que, se eu tiver uma consulta
complexa, poderei dividi-la e distribuir
a carga entre as instâncias do RDS para que elas possam
assumir parte dessa folga.
Como isso funciona?
Portanto, primeiro você
precisa se certificar de que há conectividade entre o cluster
do Redshift e as instâncias do RDS ou do Aurora com as quais deseja se comunicar.
Agora, você precisa ter
certeza de que eles estão na mesma sub-rede VPC ou usar o emparelhamento VPC
para torná-los visíveis um para o outro.
Novamente, o emparelhamento de VPC só funcionará se você não
tiver intervalos de endereços IP sobrepostos entre os dois.
Como acessá-lo?
Portanto, o Redshift precisa saber como fazer login
e acessar essas instâncias do RDS ou do Aurora, certo?
Portanto, as credenciais para fazer isso
devem ser armazenadas no AWS Secrets Manager para que isso funcione.
Em seguida, inclua esses segredos na função IAM que você
atribui ao cluster Redshift para
acessar esses bancos de dados externos.
Para criar uma tabela externa
que atinja essas tabelas externas do RDS ou do Aurora,
você pode dizer CREATE EXTERNAL SCHEMA.
E você também pode usar essa mesma sintaxe para conectar
o S3 ou o Redshift Spectrum.
Portanto, lembre-se de que eu disse anteriormente que isso não era apenas
para federar ao RDS no Aurora,
você também pode federar a data lakes dessa forma, com a mesma ideia.
À direita, a propósito,
há um exemplo da função IAM que inclui
o acesso ao AWS Secrets Manager, necessário para acessar
esses bancos de dados externos.
E se você quiser ter uma
visão rápida de quais esquemas externos
estão disponíveis e definidos no momento, a visualização SVV_EXTERNAL_SCHEMAS
conterá essa lista para você.
Vamos dar uma olhada em um exemplo aqui.
Agora, lembre-se de que, com as consultas
federadas, você só tem acesso de leitura
a essas fontes de dados externas e pode incorrer em custos
adicionais nesses bancos de dados externos com base no tráfego e na carga
que você está colocando neles.
Portanto, ele não é fornecido gratuitamente como parte do Redshift.
Qualquer carga que você estiver colocando
no Aurora, no RDS ou no data lake será adicional.
Portanto, lembre-se de que você pode consultar o RDS e o Aurora a partir
do Redshift, mas não o contrário.
Essa é uma conexão unidirecional
e é uma conexão somente de leitura do Redshift para
o RDS no Aurora.
Vamos dar uma olhada neste exemplo à direita.
Portanto, aqui estamos dizendo CREATE EXTERNAL SCHEMA, apg.
Portanto, vamos nos referir a essa tabela externa
como apg em minhas consultas do Redshift aqui.
No Postgres, isso significa
que vou falar com um banco de dados Postgres no RDS
ou no Aurora, e o nome do banco de dados
com o qual estou falando se chama
database-1.
A tabela do banco de dados com a qual estou falando
é chamada myschema.
No entanto, estou renomeando-o para apg aqui.
Em seguida, dizemos URI com o ponto de extremidade para o nome de host do Aurora
com o qual estou falando.
Eu passo na função de IAM que vimos no slide anterior.
Isso inclui todas as coisas do Secrets Manager de que
preciso e, em seguida, o ARN do segredo em si, que é necessário
para se conectar à instância do Postgres Aurora.
Depois de fazer isso, posso acessar essa tabela externa.
Como em qualquer outra tabela,
posso dizer SELECT count(*) FROM apg. item de linha.
E o apg novamente está se referindo a essa tabela externa do Postgres,
myschema, no banco de dados database-1 no Postgres remotamente, e ela funciona como
qualquer outra tabela nesse ponto.
Muito legal.
Em resumo, isso é o Redshift Federated Queries.
Algo que o exame espera que você saiba.
