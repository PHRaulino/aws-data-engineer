é um serviço de gerenciamento de chaves do AWS.
Por isso, temos usado muito essa criptografia
sem saber, mas sempre que você ouvir falar em
criptografia quando tiver um serviço
da AWS, provavelmente será a criptografia KMS.
O objetivo é que, com esse serviço KMS, o AWS
gerencie as chaves de criptografia para nós.
E isso é ótimo, pois
significa que temos menos coisas para fazer.
Portanto, o KMS é, obviamente,
totalmente integrado ao IAM para autorização e nos oferece
maneiras muito fáceis de controlar o acesso aos nossos dados se
eles estiverem criptografados com o KMS.
A vantagem de usar o AWS KMS é que você pode
auditar cada chamada de API feita para usar suas chaves por
meio do CloudTrail,
algo que pode ser testado no exame.
Além disso, o KMS
pode ser usado sem problemas na maioria dos serviços da AWS.
Assim, por exemplo, se você quiser criptografar os dados em
repouso em um volume EBS, basta ativar a integração do KMS.
O mesmo vale para o S3, o mesmo vale para o RDS, o mesmo
vale para o SSM e o mesmo vale para praticamente todos os serviços
que exigem criptografia.
A ideia é que, com o KMS, você também pode usá-lo.
E se você tiver dados secretos, nunca
os armazene em texto simples, ou seja, exatamente
como estão.
Especialmente em seu código.
Portanto, se você quiser usar o
KMS, também poderá usar o KMS por meio de chamadas de API.
Você pode usar a CLI do AWS ou o SDK.
Isso significa que você pode criptografar
qualquer coisa que seja secreta para você com uma chave KMS.
E esses segredos criptografados podem ser, por exemplo,
armazenados em seu código ou em variáveis de ambiente.
Esse é um padrão muito melhor.
Agora, vamos falar sobre os diferentes
tipos de chaves KMS disponíveis para você.
Portanto, agora ela é chamada de chave KMS.
A propósito, ela costumava
ser chamada de chave mestra do cliente KMS, mas era confusa porque também
há as chaves gerenciadas pelo cliente, como veremos
em um segundo momento.
Portanto, agora falamos apenas sobre as chaves KMS.
Portanto, temos dois tipos de chaves KMS.
Temos as chaves KMS simétricas, o que significa
que há apenas uma única chave criptografada que é usada para
criptografar e descriptografar dados.
Portanto, qualquer serviço do AWS que seja
integrado ao KMS usará chaves simétricas.
A ideia é que, quando criamos ou usamos uma chave simétrica KMS,
nunca temos acesso à chave em si, certo?
Tudo o que fazemos é usar as chamadas da API do
KMS para aproveitar e usar essa chave.
O segundo tipo de chave disponível no KMS é chamado
de chaves assimétricas.
Isso significa que você tem duas chaves.
Você tem uma chave pública que é usada para criptografar dados
e uma chave privada usada para descriptografar dados.
Portanto, isso é usado quando você tem operações do tipo criptografar/descriptografar
ou assinar/verificar.
E, nesse caso,
você pode fazer o download da chave pública do
KMS, mas pode usar o acesso à chave privada.
Você só pode usar chamadas
de API contra para acessar a chave privada.
Portanto, os casos de uso de um tipo de chave assimétrica
são quando você deseja que a criptografia seja feita
fora da sua nuvem AWS por usuários que não podem
ou não têm acesso à chave da API do KMS.
Nesse caso, eles usarão a chave pública
para criptografar os dados.
Envie-o para você.
E você, em sua conta,
usaria a chave privada da AWS para descriptografar esses dados.
Portanto, no mundo das chaves KMS,
você tem diferentes tipos de chaves KMS.
A primeira são as chaves de propriedade da AWS.
Elas são gratuitas, e esse é o tipo de chave que você usaria
ao usar o tipo de criptografia SSE-S3 ou SSC DynamoDB,
em que você tem a opção, por exemplo, de escolher uma
chave de propriedade do DynamoDB.
Portanto, esses não são realmente
KMS porque você não os vê, mas
são tipos de chaves de criptografia no AWS.
Em seguida, você tem as chaves gerenciadas da AWS, que são gratuitas, e você
as reconhecerá porque elas
começam com a barra da AWS e, em seguida, com o nome do serviço.
Por exemplo, AWS/RDS ou AWS/EBS ou,
neste exemplo, AWS/DynamoDB.
Eles são gratuitos e você pode usá-los como quiser,
mas somente dentro do serviço ao qual estão atribuídos.
Em seguida, você tem suas próprias chaves gerenciadas pelo
cliente e suas chaves personalizadas, e elas custam US$ 1 por mês.
E se quiser importá-los também, você pode importá-los,
e eles custam US$ 1 por mês.
O KMS também tem um preço em que você pagará
por cada chamada de API feita para o serviço KMS, que
é de cerca de 3 centavos por 10.000 chamadas de API.
Você também tem rotação automática de chaves.
Portanto, se for uma chave KMS gerenciada pela AWS,
ela será automática a cada um ano.
E, se for uma chave gerenciada pelo cliente,
você poderá ativar a rotação automática e definir o período,
e também poderá ter uma rotação sob demanda da chave.
E se for uma chave KMS importada, você
só poderá girá-la manualmente.
E, para isso, você precisa usar um alias.
Portanto, as chaves KMS têm escopo por região.
Isso significa que, se você tiver um volume EBS
criptografado com a chave KMS em uma região, por exemplo, EUS2, se quiser copiá-lo
para uma região diferente, será necessário executar
várias etapas.
Antes de mais nada, precisamos tirar um instantâneo desse volume do EBS.
E se tirarmos um instantâneo de um instantâneo criptografado,
esse instantâneo em si também será criptografado
com a mesma chave KMS.
Em seguida, para copiar o instantâneo para outra região, precisamos
criptografar novamente o instantâneo usando
uma chave KMS diferente.
E isso é algo que a AWS fará por você.
Mas a mesma chave KMS não pode estar em duas regiões.
Portanto, agora temos um snapshot do
EBS, que está criptografado com o KMS com uma chave diferente
e reside em outra região.
Agora, restauramos
o snapshot em seu próprio volume EBS com
KMS e sua chave KMS B na região AP sudeste dois.
Agora, outra coisa que
precisamos saber é sobre as políticas de chave KMS.
Portanto, isso serve para controlar o acesso às suas chaves KMS.
É semelhante a uma política de bucket do S3.
Com a diferença de que, se você não tiver a política de
chave KMS em sua chave KMS, ninguém poderá acessá-la.
Portanto, com relação a isso, temos dois tipos de políticas de chave KMS.
Temos a política padrão e ela é criada
se você não fornecer uma política
de chave KMS personalizada específica.
E a ideia é que o padrão permita
que todos em sua conta acessem essa chave.
Isso significa que, se você tiver uma política de IAM que permita que um usuário
ou função acesse essa política principal, não há problema.
Mas, se quiser ter controles mais específicos sobre isso,
poderá usar uma política de chave KMS personalizada.
No qual você define os usuários
e as funções que podem acessar sua chave KMS.
E você define quem pode administrar a chave.
E isso é especialmente útil se
você quiser fazer acesso entre contas para sua chave KMS, porque
podemos autorizar outra conta a usar nossa chave KMS.
Então, quando usamos isso?
Bem, por exemplo,
se quisermos copiar instantâneos criptografados entre contas.
Assim, criamos um instantâneo criptografado com nossa própria chave KMS, que é
uma chave gerenciada pelo cliente.
Deve ser assim porque precisamos anexar uma
política de chave personalizada.
Em seguida, anexamos uma política de chave
KMS para autorizar o acesso entre contas.
A aparência é a seguinte.
Em seguida, compartilhamos o instantâneo criptografado
com a conta de destino.
E, em seguida, na conta de destino, criamos
uma cópia do instantâneo e a criptografamos
com uma chave gerenciada pelo cliente diferente nessa
conta de destino.
Em seguida, podemos criar um volume
a partir do snapshot na conta de destino e pronto.
Portanto, são muitas as informações sobre
o KMS, mas vamos colocar a mão
na massa para aprender um pouco mais sobre ele.
