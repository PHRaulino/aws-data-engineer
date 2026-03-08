Então, primeiro,
Para isso, clique em configurações de conta no lado esquerdo.
Você encontrará a política de senha e poderá editá-la.
Portanto, aqui, podemos usar a política de senha
padrão do IAM, que contém esses tipos de requisitos,
ou podemos personalizar a política de senha e
forçar um comprimento mínimo de senha.
Também podemos exigir letras maiúsculas,
letras minúsculas, um número e um caractere não alfanumérico.
Também podemos ativar a expiração de senhas para,
por exemplo, expirar após 90 dias, ou
que a expiração de uma senha exija redefinições
administrativas, ou podemos permitir que os usuários alterem suas
próprias senhas ou podemos
impedir a reutilização de senhas.
Portanto, esse processo de senha pode ser editado diretamente
no console do IAM, e essa é a primeira parte da segurança.
A segunda parte
trata da configuração da autenticação
multifator para sua conta raiz.
Portanto, se você clicar no nome
da conta e, em seguida, clicar em credenciais de segurança, se estiver
conectado com o usuário root, verá
minhas credenciais de segurança de usuário root.
Agora, há uma maneira
de proteger o usuário raiz, que é
a conta mais importante da sua conta da AWS, e você pode protegê-lo
usando a autenticação multifator.
Agora, para que você saiba, vou fazer isso e
demonstrar como funciona na sua
frente, mas já tive alunos que se bloquearam em suas
contas porque perderam o acesso ao dispositivo
de autenticação multifator.
Portanto, se você acha que está correndo o risco de perder
seu iPhone ou qualquer outra coisa, não faça isso, ok?
Basta manter seu telefone com você e assistir ao meu vídeo.
Se você quiser praticar comigo, pode
fazê-lo também.
E você também pode excluir o dispositivo MFA depois de ativá-lo.
Certo, mas vamos prosseguir e atribuir um dispositivo MFA.
Portanto, chamarei este de meu iPhone porque
é o que tenho, mas você pode dar o nome
que quiser.
Em seguida, você pode selecionar o tipo de dispositivo MFA.
Portanto, pode ser um aplicativo
autenticador, que é algo que
vou usar, mas também pode ser uma chave de segurança ou um token TOTP de hardware.
Portanto, vou usar um aplicativo autenticador
porque ele será virtual.
E agora vamos para a configuração do aplicativo.
Portanto, há uma lista de aplicativos compatíveis bem aqui.
Você pode encontrar aqui para Android e
para iOS que sabemos que funcionam bem com a AWS.
Por isso, vou usar o Twilio do Authenticator,
que é um aplicativo de que gosto.
Então, o que preciso fazer é iniciar o aplicativo
no meu telefone e clicar em mostrar o código QR.
Portanto, quando você receber
um código QR, precisará digitalizá-lo diretamente no seu telefone.
Portanto, para isso, você
adiciona uma conta, escaneia o código
QR aqui e, uma vez escaneado, ele adicionará a conta e começará
a nomeá-la.
Então, vamos salvar isso, parece bom.
E então temos acesso ao código MFA.
Portanto, há o primeiro, o primeiro código MFA, ou seja, 301935.
Portanto, este é um código gerado pelo meu iPhone em tempo real.
E esse código mudará com o tempo.
E a razão pela qual esses dois códigos são solicitados pela AWS
é que ela quer ter certeza de que o dispositivo
MFA está configurado corretamente e que os códigos são precisos.
Portanto, o segundo código é 792843.
E, é claro, haverá diferenças em seu dispositivo.
Depois de inserir esses dois códigos, você clica em adicionar MFA.
E, como você pode ver, podemos acessar até
oito dispositivos MFA atualmente, e você pode rolar para baixo
e vê-los bem aqui na lista.
Portanto, a autenticação multifator, MFA, é chamada de
meu iPhone, que foi criada agora.
Portanto, se você quiser removê-lo, poderá removê-lo e assim por diante.
Mas, então, como usamos a MFA?
Bem, se eu sair do AWS e fizer login
novamente, usarei minha conta
de roteador e minha senha.
Agora, depois de fazer um login bem-sucedido,
tenho o código MFA para inserir.
Então, abro meu
aplicativo, insiro o código que vejo e pressiono enviar.
E, dessa forma, o IAM fez login.
E isso é perfeito porque, bem, tínhamos um nível
extra de segurança em nossa conta.
Então é isso para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
