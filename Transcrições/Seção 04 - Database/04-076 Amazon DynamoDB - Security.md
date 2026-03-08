Então, vamos falar sobre a segurança
Portanto, para fins de segurança, temos endpoints de VPC
que estarão disponíveis
para acessar o DynamoDB sem usar a Internet pública
e mantendo todo o tráfego apenas dentro de sua VPC.
O acesso ao DynamoDB é totalmente controlado pelo IAM,
o que o torna uma ótima opção de banco de dados no AWS.
E você tem criptografia
em repouso usando o AWS KMS ou em trânsito usando SSL e TLS.
Há recursos de backup e restauração disponíveis.
Você tem dois deles.
Portanto, você tem recuperação
point-in-time, ou seja, PITR, assim como o RDS,
e não há impacto no desempenho,
ou podemos fazer um backup normal e restaurá-lo.
Agora, há o conceito de tabelas globais e DynamoDB.
Portanto, a ideia é que você tenha uma tabela de alto desempenho
totalmente replicada, multirregional e multiativa no DynamoDB.
E como habilitá-lo?
Bem, primeiro você precisa habilitar os fluxos do DynamoDB.
Portanto, embora o DynamoDB seja um serviço
em nuvem, é possível obter uma simulação do DynamoDB
em seu computador local, chamada
DynamoDB local, e a ideia
é que você tenha um banco
de dados DynamoDB local que possa ser usado para desenvolver
e testar seus aplicativos localmente sem
usar o serviço da Web do DynamoDB, o que é muito,
muito útil.
E se você quiser migrar dados de e para o DynamoDB, o AWS
Database Migration Service é
uma ótima opção.
Assim, por exemplo,
de MongoDB para DynamoDB,
ou Dynamic V2 Oracle, mySQL, S3 e assim por diante.
Agora, outro recurso que você precisa entender
sobre o DynamoDB é o acesso de grão fino.
Assim, por exemplo, se você tiver
clientes e aplicativos, da Web ou móveis,
e eles precisarem acessar diretamente nossa tabela DynamoDB,
não queremos dar a eles permissões e funções
de IAM, usuários diretamente da AWS, pois isso será realmente
ineficiente e uma falha de segurança.
Em vez disso, usaremos um provedor de identidade.
Pode ser o Amazon Cognito User Pools, o login
do Google, o login do Facebook, o
open ID connect, o SAML ou qualquer outro.
E os usuários, no fluxo simplificado, farão login
com esses provedores de identidade e terão
o recurso de trocar as
credenciais que acabaram de receber
por credenciais temporárias da AWS.
E a ideia é que, por serem temporários,
eles são mais seguros.
E, com eles, podem ser associados a uma função de IAM, mas
essa função de IAM deve ser restrita
porque, agora que nossos clientes e aplicativos
podem acessar nossa tabela do DynamoDB,
você quer que eles possam fazer operações
somente nos dados que possuem.
Então, como fazemos isso,
esse controle de acesso de grão fino?
Bem, temos um login federado para obter credenciais
temporárias e, em seguida,
podemos criar uma função de IAM, e essa função
de IAM terá uma condição.
E essa condição levará ao que o usuário pode fazer.
Portanto, aqui está um exemplo de política.
Portanto, nessa política, o usuário pode obter itens,
obter itens em lote, consultar, colocar itens, atualizar
itens, excluir itens e excluir itens em lote em uma tabela específica.
Mas há uma condição aqui.
E a condição está
dizendo: "Ei, somente se as chaves principais corresponderem ao DynamoDB e,
em seguida, às pseudovariáveis de identidade do conector, que serão substituídas em
tempo de execução pelo usuário específico".
Portanto, o que estamos dizendo é que,
com o LeadingKey, limitamos apenas o acesso no nível da linha para os usuários
com base no valor da chave primária.
Portanto, garantimos que os usuários só possam modificar
e acessar seus próprios dados.
E você também pode especificar condições nos atributos, o
que limitaria os atributos específicos que um
usuário pode ver na tabela do DynamoDB, certo?
Portanto, para resumir, você tem um controle de acesso
de granulação fina usando um login federado
e especificando uma condição no LeadingKeys, se quiser
limitar no nível da função ou dos atributos,
se quiser limitar no nível da coluna, no nível do atributo.
Muito bem, isso é tudo para esta palestra.
Espero que você tenha gostado.
E eu o verei na próxima palestra.
