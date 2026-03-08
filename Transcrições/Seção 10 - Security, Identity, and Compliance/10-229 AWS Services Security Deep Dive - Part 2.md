Então, o que você obtém por meio do RDS?
Bem, os bancos de dados RDS são implantados em sua VPC, portanto,
isso lhe proporcionará isolamento de rede.
Em seguida, você pode usar os grupos
de segurança anexados às instâncias
do RDS, o que controlará o acesso às instâncias do banco
de dados em portas específicas a partir de intervalos de IPs específicos,
como outsider ou outros grupos de segurança.
Além disso, você pode usar o KMS para fornecer
criptografia em repouso dos dados no RDS e
pode usar o SSL para a conexão JDBC para fornecer criptografia
em voo ao conversar com o banco
de dados RDS.
As políticas de IAM não oferecem proteção
a partir do banco de
dados, elas oferecem proteção à própria API do RDS.
E a autenticação IAM é um meio de autenticação
compatível com o PostgreSQL, o MySQL e o MariaDB.
Portanto, é necessário gerenciar as permissões de
usuário no próprio banco de dados.
Portanto, isso não o torna tão bom quanto o DynamoDB
em termos de integração com o IAM.
Assim, depois que os usuários são
criados, seja usando a autenticação IAM ou apenas usuários manuais
por meio da API do Postgres e do MySQL, no
banco de dados você deve dizer que este
usuário tem acesso a esta tabela.
Mas isso não é algo que você gerencia por meio do IAM.
Isso é algo que é gerenciado
pela tecnologia de banco de dados.
Há também o fato pouco conhecido
de que o Microsoft SQL Server e o Oracle suportam
algo chamado TDE, chamado Transparent
Data Encryption.
E ele pode ser ativado com o KMS para fornecer
mais criptografia aos seus dados,
ainda mais, certo?
Então é isso para o RDS.
Espero que isso faça sentido para você.
Espero que isso não seja novidade.
Para o Aurora, bem, ele é de fato muito semelhante ao RDS.
Temos VPC para obter isolamento de rede, grupos de segurança
para controlar quem tem acesso ao nosso banco de dados, KMS para
obter criptografia em repouso, SSL para
obter criptografia em voo, autenticação
IAM para Postgres e MySQL, e precisamos gerenciar as permissões
de usuário dentro do próprio banco de dados.
Lembre-se de que o Aurora não oferece
suporte a nada como Oracle ou Microsoft SQL Server.
No momento, somente o Postgres
e o MySQL têm APIs compatíveis.
Muito bem, deixando o banco de dados, vamos para o Lambda.
Então, Lambda, como isso funciona?
Há muita segurança em torno dele.
Em primeiro lugar, sua função
Lambda deve ter uma função IAM associada a ela.
Portanto, cada função Lambda terá sua própria função
IAM, que definirá as permissões do que ela pode fazer.
Bem, por que você precisa de permissões?
Bem, porque o Lambda extrairá dados das fontes
e os enviará aos alvos.
Portanto, basicamente, as funções
de IAM associadas às suas funções Lambda o ajudarão
a decidir o que a função Lambda
pode fazer em termos de fontes e alvos.
O Lambda tem integração com o KMS para criptografia de segredos.
Assim, por exemplo,
se você quiser passar segredos para a sua função Lambda,
poderá usar variáveis criptografadas do KMS e executar
a função de descriptografia dentro
da sua função AWS Lambda, desde que ela
tenha as funções IAM corretas.
Você também pode usar o armazenamento de
parâmetros do SSM para armazenar configurações em
sua função AWS Lambda e até mesmo criptografar os segredos no SSM com o KMS.
Ele tem integração com os registros do CloudWatch.
Novamente, certifique-se de que a função do IAM esteja correta.
E você pode implantar suas funções do AWS Lambda na sua VPC,
caso precise acessar recursos de dentro da sua VPC.
Portanto, vimos anteriormente que o RDS é implantado em sua VPC.
Se precisar de uma função Lambda para, basicamente,
interagir com seu banco de dados RDS,
você implantaria sua função Lambda
diretamente em seu VPC privado.
Muito bem, agora temos o Glue.
Portanto, para controlar o acesso ao serviço Glue, você
pode usar as políticas do IAM para isso.
Isso é como qualquer outro serviço da AWS.
E você também pode configurar o Glue para acessar seus bancos de dados
com JDBC somente usando SSL, o que significa que
você quer que a criptografia seja ativada
enquanto a conexão do Glue com seu banco de dados
estiver sendo feita, certo?
Isso significa que seus dados durante o voo estão sendo criptografados.
É muito importante entender o Data Catalog
e lembrá-lo do ponto de vista da segurança.
Em primeiro lugar, você pode criptografar o Data Catalog pelo KMS.
Isso significa que você garante que
seus dados sejam criptografados
em repouso, mas também pode criar políticas de recursos que
protejam os recursos do Data Catalog.
Portanto, isso é muito semelhante a uma política de bucket do S3.
Portanto, quando temos uma política de bucket
do S3, nosso bucket do S3 fica protegido contra acesso indesejado,
e podemos definir isso na política de bucket.
Eles terão o mesmo conceito com
os recursos do Data Catalog.
Podemos criar políticas de recursos para proteger esses recursos, e isso
é algo que você deve lembrar ao fazer o exame.
A senha da conexão pode ser criptografada pelo
KMS para aumentar a segurança.
E, por fim, todos os dados gravados pelo Glue também podem ser criptografados.
Portanto, temos uma configuração de segurança para
o modo de criptografia S3, de modo que podemos
ter a criptografia do lado do servidor S3 ou a criptografia
do lado do servidor KMS.
Podemos ativar qualquer criptografia do CloudWatch para os registros.
E, por fim, os marcadores de trabalho também podem ser criptografados.
Portanto, lembre-se de que, ao entrar no
Glue, muitas coisas podem ser
criptografadas e o Data Catalog pode ser protegido
usando uma política de recursos.
E, por fim, o Glue pode ser configurado
para acessar seus bancos de dados somente por meio de SSL para manter
a criptografia em trânsito.
Então é isso para esta parte dois da Segurança dos serviços da AWS.
Vejo você na próxima palestra para a terceira parte.
