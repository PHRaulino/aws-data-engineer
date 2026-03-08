- Stephane] Bem-vindo ao primeiro mergulho
O primeiro é chamado de IAM.
Portanto, IAM significa gerenciamento de identidade e acesso.
É um serviço global porque, no IAM, vamos
criar nossos usuários e atribuí-los a um grupo.
Portanto, já usamos o IAM sem saber que, quando
criamos uma conta, criamos uma conta raiz, que foi
criada por padrão.
Esse é o usuário raiz de nossas contas.
E a única coisa para a qual você deve usá-lo é para
configurar sua conta, como faremos agora.
Mas então você não deve mais usar essa conta,
nem mesmo compartilhá-la.
Em vez disso, o que você deve fazer é criar usuários.
Portanto, você criará usuários no IAM,
e um usuário representa uma pessoa na sua organização.
E os usuários podem ser agrupados, se isso fizer sentido.
Vamos dar um exemplo: temos uma organização
com seis pessoas.
Você tem Alice, Bob, Charles, David, Edward e Fred, portanto,
todas essas pessoas estão em sua organização.
Agora Alice, Bob e Charles trabalham juntos.
Todos eles são desenvolvedores.
Portanto, vamos criar um grupo chamado
desenvolvedores de grupo que reagrupa Alice,
Bob e Charles.
E acontece que David e Edward também trabalham juntos.
Portanto, vamos criar um grupo de operações.
Agora temos dois grupos no IAM.
Agora os grupos só podem conter usuários, não outros grupos.
Portanto, é muito importante entender isso.
Os grupos contêm apenas usuários.
Agora, alguns usuários não precisam pertencer a um grupo.
Por exemplo, o Fred aqui está sozinho, ele
não corresponde a nenhum grupo.
Essa não é a melhor prática.
Mas isso é algo que você pode fazer no AWS.
Além disso, um usuário pode pertencer a vários grupos.
Isso significa que, por exemplo, se você sabe
que Charles e David trabalharam
juntos e que eles fazem parte da sua equipe de
auditoria, você pode criar um terceiro grupo com Charles e David.
E, como você pode ver, neste exemplo,
Charles e David fazem parte de dois grupos diferentes.
Portanto, essas são as configurações possíveis para o IAM.
Então, por que criamos usuários e por que criamos grupos?
Bem, porque queremos permitir que eles usem nossas contas
da AWS e, para isso, precisamos
dar a eles permissões.
Portanto, os usuários ou grupos podem receber o que é
chamado de documento JSON.
Vou lhe mostrar agora mesmo o que significa uma política,
uma política de IAM.
Portanto, a aparência é a seguinte.
Portanto, você não precisa ser um programador.
Isso não é programação.
Isso apenas descreve, em linguagem simples, o que um usuário
tem permissão para fazer ou o que um grupo e todos os
usuários desse grupo têm permissão para fazer.
Portanto, neste exemplo, podemos ver que permitimos
que as pessoas usem o serviço EC2 e o descrevam, usem o serviço
de balanceamento de carga elástica
e o descrevam e usem o CloudWatch.
Agora, veremos o que significam o balanceamento de carga
elástica do EC2 e o CloudWatch, mas por meio desse documento JSON que tem
a seguinte aparência.
Estamos permitindo que nossos usuários usem alguns serviços no AWS.
Portanto, essas políticas nos ajudarão a definir as
permissões dos nossos usuários.
Assim, na AWS, você não permite que todos façam tudo o que seria catastrófico,
porque um novo usuário poderia
basicamente lançar muitos serviços que custariam muito dinheiro
ou seriam válidos para a segurança.
Portanto, na AWS, você aplica um princípio chamado princípio
do menor privilégio.
Assim, você não concede mais permissões do que o usuário precisa.
Portanto, se um usuário precisar apenas de acesso a três serviços,
basta criar uma permissão para esse usuário.
Agora temos uma visão geral do IAM.
Na próxima aula, vamos
praticar a criação de usuários e grupos.
