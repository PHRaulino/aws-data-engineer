Hey, estamos na terceira
parte de
E estamos começando com o EMR.
Agora, o EMR é algo que será extremamente
importante
para entender a segurança ao fazer o
exame.
Portanto, você precisa prestar muita
atenção nos
próximos dois slides e se lembrar
de tudo o que vou dizer.
Então, vamos em frente.
Portanto, primeiro, como o EMR provisiona
algumas instâncias do
EC2, é possível provisionar um par de
chaves
para gerenciar o acesso SSH a essas
instâncias.
Também podemos anexar funções de IAM a
essas instâncias do EC2.
Por quê? Bem, porque talvez queiramos
acessar o S3 usando
o EMRFS para fazer a solicitação, ou
talvez você queira
gravar dados de volta no S3 por qualquer
motivo.
Portanto, você precisa garantir que as
funções
do IAM tenham acesso ao S3, obviamente.
Se estiver acessando o DynamoDB e precisar
usar o Hive para isso, será necessário
verificar novamente se as instâncias do
EC2
têm permissão para acessar o DynamoDB.
E, mais uma vez, essa função do IAM é
crucial para alcançar exatamente isso.
Agora, para grupos de segurança, há dois
tipos.
Você tem o primeiro tipo, que é para o nó
mestre, e o segundo tipo para os nós do
cluster,
que representa o nó principal e o nó de
tarefa.
E o motivo pelo qual temos grupos de
segurança é permitir a comunicação entre
os nós,
porque, digamos, você está executando um
trabalho
do Spark ou um trabalho de análise
de correspondência distribuída ou qualquer
coisa que
exija que os nós conversem entre si.
Em seguida, você precisa se certificar de
que as regras de segurança da rede
estejam em vigor para permitir essas
comunicações.
Portanto, os grupos de segurança são
extremamente importantes.
Em termos de autenticação,
temos a autenticação Kerberos.
E isso é útil quando você deseja conectar
seu mecanismo de autenticação ao Active
Directory.
E, por fim, há uma maneira de
código aberto de gerenciar a segurança no
EMR para autorização, chamada Apache
Ranger.
Portanto, trata-se de RBAC (Role Based
Access), e você
precisa configurá-lo em uma instância
externa do EC2
e, em seguida, conectá-lo ao seu cluster
EMR.
Portanto, isso não é algo que possa ser
configurado diretamente no EMR.
Você precisa configurar externamente no
EC2 e
conectá-lo, configurá-lo com seu cluster
EMR.
Eu recomendaria a leitura desse blog se
você
quiser saber mais sobre essa segurança de
EMR.
Acho que é um blog muito interessante
de se ler e algo que pode
ser muito útil para o seu exame.
Ok, o próximo passo para o EMR será a
criptografia do EMR, e isso é muito
importante.
Você se lembra de tudo o que eu vou dizer.
Portanto, temos criptografia de dados em
repouso para EMRFS.
Portanto, EMRFS é quando seus dados
residem no Amazon S3.
Por isso, precisamos criptografar os dados
no Amazon S3.
Portanto, temos três opções diferentes.
Temos a criptografia SSE-S3, SSE-KMS ou
até mesmo a criptografia do lado do
cliente.
Portanto, três tipos.
Como você pode ver, o quarto tipo de
SSE-C não é compatível com o EMRFS.
Você também pode criptografar os dados em
seus discos locais.
Portanto, usando esse EMRFS, você tem a
criptografia acontecendo
no Amazon S3 e no seu disco local.
Vamos falar mais detalhadamente sobre esse
disco local.
Portanto, você tem diferentes tipos de
criptografia para seu disco local.
A primeira é a criptografia HDFS de código
aberto, que consiste em confiar em
qualquer
criptografia criada para o ecossistema do
Hadoop
e usá-la em seu cluster do Hadoop.
Mas você também pode usar alguns
mecanismos
de criptografia mais nativos da AWS.
Portanto, se você tiver um armazenamento
de instância
EC2, o que significa que o armazenamento
está
fisicamente conectado à instância EC2,
poderá usar
a criptografia NVMe ou a criptografia
LUKS.
Está bem? Lembre-se dessas duas coisas.
Em seguida, você tem um volume EBS.
Portanto, isso significa que seu
armazenamento não
está fisicamente conectado à instância do
EC2.
Isso significa que ele está conectado por
meio da rede.
Então, você pode ter a criptografia EBS,
a criptografia nativa usando o KMS.
E o bom disso é que ele funciona para
o volume raiz de sua instância do EC2.
É muito importante lembrar.
Mas você também pode usar a criptografia
Lux.
E, nesse caso, ele não funciona com
raízes.
Portanto, se você chegar a um cluster EMR
que tenha
o suporte do EBS e quiser garantir que o
volume do EBS seja criptografado,
inclusive o volume raiz.
Então, você precisa usar a criptografia
KMS
do EBS, e não a criptografia LUKS.
Ok, isso é para o repouso.
Agora, para o trânsito, podemos ter
criptografia entre os nós, de modo
que a comunicação entre os
nós seja criptografada usando SSL.
E você também pode garantir que qualquer
tráfego feito a partir
do EMRFS, ou seja, entre o S3 e os nós do
cluster, também será criptografado de
ponta a ponta usando TLS.
Esse diagrama pode ser útil para lembrar
as coisas e colocá-las em perspectiva.
E isso vem diretamente da documentação do
EMR
para as opções de criptografia de dados.
Portanto, como eu disse, você precisa se
lembrar de
tudo o que acabei de dizer sobre EMR.
Esses serão alguns pontos muito valiosos
para o
exame, portanto, espero que tenham sido
úteis.
A próxima tecnologia será o OpenSearch
Service.
Portanto, temos o isolamento da rede por
meio do uso do Amazon VPC.
E se quisermos gerenciar o acesso ao nosso
cluster do OpenSearch,
poderemos usar uma política do OpenSearch
para gerenciar a segurança.
Por exemplo, para restringir por endereço
IP.
Temos segurança de dados criptografando os
dados em repouso usando o KMS.
E temos criptografia em trânsito usando os
pontos de extremidade HTTPS do OpenSearch
Service,
que, nos bastidores, usa criptografia TLS.
Para autenticação, temos a autenticação
baseada em IAM ou Cognito.
Por exemplo, se usarmos o Cognito,
permitiremos
que o usuário final faça login no
Open Search Dashboards por meio de um
provedor de identidade corporativa, como o
Microsoft
Active Directory, usando o protocolo SAML.
Portanto, observe que são muitas
palavras-chave, mas é
importante entendê-las e conhecê-las para
o exame.
Portanto, agora temos o Redshift.
E também é muito, muito, muito importante
conhecer o Redshift em termos de
segurança.
Portanto, a VPC fornecerá isolamento de
rede
para o Redshift e, além disso, você
poderá aplicar grupos de segurança de
cluster
para garantir o controle sobre quais
máquinas
podem acessar o cluster do Redshift.
Você obtém criptografia em voo porque está
usando o driver JDBC habilitado com SSL.
Portanto, você pode criptografar seus
dados diretamente
no Redshift e pode criptografar em repouso
usando o KMS ou um dispositivo HSM.
Portanto, se você usar um dispositivo
HSM para criptografar em repouso no
Redshift, precisará estabelecer uma
conexão entre
o dispositivo HSM e o Redshift.
Tudo isso está bem documentado na
documentação da AWS.
O que você precisa lembrar é que o
Redshift é uma tecnologia que pode usar o
KMS, e dessa forma ele é gerenciado pelo
AWS, ou podemos usar um dispositivo HSM
personalizado
ou um módulo de segurança de hardware.
Ele também é compatível com SSE-S3 usando
chaves gerenciadas padrão.
E você pode anexar funções de IAM para o
Redshift,
basicamente permitindo que você
descarregue ou leia dados do S3.
Então, tudo bem, finalmente, se você usar
um
comando copy ou unload, poderá fazer
referência às
funções do IAM que atribuiu ao Redshift
ou,
alternativamente, se quiser herdar suas
próprias credenciais de
chave, poderá colar sua própria chave de
acesso
e chave secreta diretamente em suas
instruções SQL,
e o Redshift as aproveitará ao ler dados
do S3 ou gravar dados no S3.
Ok, espero que isso faça sentido.
Novamente, certifique-se de que você
realmente conhece
muito bem a segurança do Redshift.
Athena, Athena é muito fácil.
Você usa as políticas de IAM para
controlar o acesso ao próprio serviço
Athena.
E os dados serão armazenados no S3 de
qualquer forma,
portanto, você herda toda a segurança que
vem do S3,
que inclui políticas de IAM, políticas de
bucket e ACLs.
Você criptografará os dados de acordo com
os centros S3.
Portanto, temos SSE-S3, SSE-KMS, e CSE
significa
criptografia no lado do cliente para KMS.
Você pode obter criptografia em trânsito,
obviamente,
porque usa certificados TLS entre o Athena
e o S3, e pode usar um
driver JBC que será habilitado por SSL.
Por fim, se você precisar de acesso
refinado, poderá
usar o próprio AWS Glue Catalog Security
para
restringir quem pode fazer o quê no
Athena.
Muito bem, isso é tudo para as tecnologias
de consulta.
Por fim, a tecnologia de visualização do
Quicksight.
Bem, você tem dois tipos de edições.
Você tem a edição Standard, na qual pode
usar os usuários do IAM para fazer login
no Quicksight ou em contas baseadas em
e-mail.
E para a edição Enterprise, você pode
usar a segurança baseada no Active
Directory para fazer login no Quicksight.
Com um Login Federado, ele também
suporta MFA ou autenticação multifator.
Você obtém criptografia em repouso e
também no SPICE.
Portanto, você obtém criptografia em
repouso no
Quicksight e no mecanismo do processador.
E, por fim, temos o Row Level Security
para controlar
qual recurso pode acessar quais linhas,
bem como o
Column Level Security para restringir o
acesso a colunas
específicas em seus conjuntos de dados
para usuários específicos.
Então, é isso para todas as tecnologias de
uso em segurança.
Pode ser chato, pode ser muita
informação, mas você precisa saber todas
essas informações para o exame.
Então, aqui está para você.
Sinta-se à vontade para não ter pressa,
revisitá-los um a
um, ler alguns blogs e se familiarizar com
eles.
Muito bem, espero que você goste.
E eu o verei na próxima palestra.
