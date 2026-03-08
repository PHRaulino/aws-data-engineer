muito simples chamado AWS Secrets Manager.
Portanto, é um serviço mais novo, destinado a armazenar
segredos, e será diferente do armazenamento de parâmetros
do SSM, porque no Secrets Manager você pode forçar a rotação de segredos
a cada X dias e, portanto, tem um cronograma de gerenciamento
de segredos melhor.
Além disso, a partir do Secrets Manager,
você pode forçar e automatizar a geração de
segredos na rotação.
E, para isso, você precisa definir uma função
Lambda que gerará esses novos segredos.
Além disso, o Secrets Manager é muito bem integrado
a diferentes serviços na AWS.
E acabei de lhe mostrar o Amazon RDS,
por exemplo, para MySQL, PostgreSQL, SQL ou Aurora.
Mas também há outros serviços com o AWS, outros bancos
de dados, que são integrados ao Secrets
Manager imediatamente.
Isso significa que o nome de usuário e a senha para entrar
no seu banco de dados são armazenados diretamente no Secrets Manager
e podem ser alternados e assim por diante.
Agora, os segredos podem ser criptografados usando o serviço KMS.
Portanto, sempre que no exame você vir Secrets,
ou integração para RDS, ou para
Aurora of Secrets, pense realmente no Secrets Manager.
Há mais um recurso que precisamos
conhecer, que é o conceito de Segredos de várias regiões.
Portanto, a ideia é que você possa replicar
seus segredos em várias regiões da AWS e o Secrets
Manager Service manterá os leitores em sincronia
com os segredos primários.
Portanto, aqui temos duas regiões.
Criamos um segredo na região primária
e ele é replicado como um mesmo segredo
em uma região secundária.
Por que faríamos isso?
Bem, várias coisas.
Número um, caso haja um problema com o US East 1, você poderá,
por exemplo, promover uma réplica do Secret
como um segredo autônomo.
E, graças ao fato de que o Secret é replicado entre as
regiões, você pode criar aplicativos para várias regiões.
Você também pode ter estratégias de recuperação de
desastres ou, se tiver um banco de dados RDS que também esteja sendo
replicado de uma região para outra,
poderá usar o mesmo segredo para acessar o mesmo banco
de dados RDS, o banco de dados correspondente, na região correspondente.
Então é isso para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
