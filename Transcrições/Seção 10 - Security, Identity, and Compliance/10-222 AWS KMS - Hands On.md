Primeiro, no lado esquerdo,
quero dar uma olhada nas chaves gerenciadas do AWS.
Você pode ver que, se eu estiver usando a criptografia
KMS ao longo deste curso, essas chaves aparecerão
bem aqui.
Portanto, podemos observar, por exemplo, o AWS EBS, e essa
é uma chave gerenciada pela
Else porque pertence ao serviço EBS.
Assim, podemos dar uma olhada aqui, como ele está sendo usado.
Portanto, há uma política de chave, e
essa política complexa define o que pode acessar essa chave.
E, é claro, como essa é uma chave do EBS AWS, você verá todas
as ações, portanto, ela pode vir de
qualquer lugar e realizar algum tipo de ação.
Mas a condição é que a conta do chamador seja
a minha e que o serviço Via seja
o serviço EC2, que
é um serviço acima do serviço EBS, certo?
Se eu olhar, por exemplo, para outra chave gerenciada pelo
AWS, por exemplo, a do SQS, e observar
a política de chave, aqui o serviço Via como condição
para minha política de chave KMS é o serviço SQS, permitindo,
portanto, somente o acesso do SQS a essa chave.
Também podemos observar a configuração criptográfica,
que mostra que essa chave é simétrica do KMS de origem e é usada para
criptografar e descriptografar dados.
Está bem.
Isso é para a chave gerenciada pelo KMS da AWS,
mas temos outros tipos.
Temos as chaves gerenciadas pelo cliente, bem como
o armazenamento de chaves personalizado.
Portanto, o armazenamento de chaves personalizado é quando queremos
usar o CloudHSM, mas isso está fora do escopo deste exame.
Portanto, não vamos analisar isso,
vamos apenas analisar a chave gerenciada pelo cliente.
Portanto, é nesse momento que queremos criar nossas próprias
chaves no KMS e não usar as gerenciadas pelo AWS.
Então, vamos criar uma chave, mas se fizermos
isso, lembre-se de que isso custará US$ 1 por mês.
Portanto, se você não quiser pagar nada, não faça isso.
Portanto, aqui para o tipo de chave, temos
várias opções, temos o tipo de chave simétrica ou assimétrica.
Portanto, se eu usar assimétrico, ele poderá ser usado para criptografar
e descriptografar ou assinar e verificar tipos de operações.
Mas isso está fora do escopo desta
palestra. Vou usar o tipo simétrico de chave KMS e usaremos a opção
de criptografia e descriptografia.
Para opções avançadas, a origem da chave
será KMS, pois queremos que o KMS crie essa
chave para nós.
Se quiséssemos importar uma
chave, esse seria o tipo externo de origem da chave ou o armazenamento de chaves personalizado
se quiséssemos ter o CloudHSM, mas, novamente, isso está
fora do escopo.
Portanto, usaremos o KMS.
E aqui, para a regionalidade, temos uma chave de região única
e uma chave de várias regiões.
Neste momento, consideraremos apenas a chave
de região única, pois esse é o tipo
de opção mais antigo e mais comum para o KMS.
Portanto, usaremos a chave de região única e clicaremos em Next.
Em seguida, temos um alias de
chave, portanto, vou usá-lo apenas como tutorial.
Clique em Next.
E aqui podemos começar a definir os principais administradores.
Portanto, se eu não definir uma, usaremos
a política de chave KMS padrão, que é o que eu quero.
Mas se você quiser ser muito específico
sobre quem pode usar essa chave e quem pode administrá-la,
é aqui que isso aconteceria.
Portanto, neste momento, não vou tomar nada
e clicar em Next.
Então você pode dizer quem pode usar essa chave?
Novamente, isso é para sua política de chave KMS.
Para ser mais específico, no momento quero permitir que
todos o utilizem se tiverem as permissões IAM corretas.
Mas, se você também quisesse ter alguma segurança
extra, poderia dizer que somente Stefan pode usar essa
chave e isso criaria uma política de chave KMS personalizada.
Mas, nesse caso, eu não quero isso.
E, como você pode ver na parte inferior,
posso escolher outras contas da AWS para acessar minha chave.
Portanto, se você tivesse, por exemplo,
o caso de uso de compartilhar um instantâneo criptografado,
um instantâneo do EBS, por exemplo, você
adicionaria outra conta para permitir o acesso à sua chave.
Portanto, resumimos tudo, temos uma chave simétrica e esta
é a política de chave, que
é o que chamo de política de chave padrão.
Isso serve apenas para ativar a permissão
de usuário do IAM, permitindo que qualquer pessoa faça qualquer recurso
no KMS, desde que tenha, é claro, permissões
do IAM para isso.
Então, vamos terminar isso.
E agora minha chave foi criada e
podemos clicar em View Key.
Agora que minha chave foi criada,
posso dar uma olhada na política da chave.
Portanto, a política de chave é exatamente assim, é uma
política de IAM para sua chave.
Mas você pode alternar para a exibição
padrão e ver um resumo melhor, como quem são os administradores
de chaves, se é permitido excluir chaves?
Quem são os principais usuários?
E outras contas podem acessá-lo?
Portanto, não tocarei nesse assunto.
Em seguida, você pode dar uma olhada na configuração criptográfica.
Não vou tocar nisso.
Tags não necessárias.
Portanto, para o rodízio de chaves, podemos ativar o rodízio automático
de chaves editando aqui e dizendo sim, está ativado,
e podemos configurar o período de rodízio de 90 dias
para muitos outros dias, até 2.560 dias.
Portanto, aqui é um ano, mas
você tem a opção de personalizá-lo.
Se você ativar essa opção, saberá as próximas datas de rotação.
E também, por exemplo,
você pode iniciar a rotação de teclas sob demanda
clicando nesse botão.
Sempre que você girar sua chave automaticamente
ou sob demanda, ela aparecerá no histórico
de rotação de chaves.
Portanto, essas opções estão
disponíveis porque criamos suas chaves diretamente do KMS.
E, finalmente, veja, finalmente, qual é o alias da minha chave?
Ele tem o nome de tutorial, portanto, posso me referir
a ele com um alias ARN,
o que será um pouco mais simples para nós.
Por fim, para ações-chave, você
pode desativá-las ou agendar a exclusão de chaves.
Portanto, temos nossa chave,
o que é ótimo, mas agora vamos usar a CLI para criptografar
e descriptografar alguns dados.
Portanto, no KMS, tenho o kms-demo-cli. sh, que nos mostrará como
usar a chamada de criptografia e descriptografia
do KMS com um exemplo.
Portanto, primeiro temos que criar um arquivo,
que chamarei de ExampleSecretFile. txt.
E com ela vou
dizer que há uma senha super secreta, ok?
Portanto, isso é o que você quiser nesse arquivo de texto.
Para mim, acabei de inserir uma senha
chamada SuperSecretPassword,
e vamos criptografá-la e descriptografá-la usando o KMS.
Portanto, a primeira coisa que você faz para a
criptografia do KMS é usar o comando encrypt.
Portanto, temos que especificar um ID de
chave, que para mim é alias/tutorial, o que corresponde
à chave que você criou no My Console.
E você pode usar o alias,
pode usar esse ID de chave aqui, ou
pode usar o ARN completo,
não importa, use o que quiser.
E então você precisa passar em texto simples
o endereço do seu arquivo.
Portanto, para mim, é o ExampleSecretFile. txt.
A saída da consulta, portanto, você está consultando
um blog de texto cifrado,
que representa o conteúdo criptografado,
e deseja o texto como está.
E, por fim, a região em que sua chave está. No
meu caso, a minha é a região de gerenciamento eu-west-2.
Isso nos dará um arquivo de base 64 que contém o conteúdo
criptografado.
Então, vamos copiar esse comando aqui,
colá-lo e executá-lo.
E agora tenho um arquivo chamado ExampleSecretFileEncrypted.
E isso representa meu arquivo criptografado, ok, na base 64, portanto,
base64.
apenas com letras e números que podemos reconhecer.
Agora, porém, vamos fazer uma decodificação de base 64 para obter
o valor binário criptografado.
Portanto, se você estiver no Windows, o comando será diferente.
Portanto, no Linux, vou executar apenas
este, mas no Windows você pode executar o outro.
Portanto, a ideia é que você
crie um arquivo chamado ExampleSecretFileEncrypted sem
uma base 64.
Então, vou copiar e colar isso.
E agora tenho um novo arquivo chamado ExampleSecretFileEncrypted.
E se eu tentar abri-lo com meu editor de texto, não
funcionará porque ele diz que
usa codificação de texto binária ou não suportada.
Portanto, esse é de fato um arquivo binário.
Portanto, esse é o tipo de arquivo secreto
que você compartilharia com alguém.
Portanto, agora quero descriptografá-la.
Portanto, isso é completamente sem sentido e não podemos
obter nenhuma informação sobre isso.
Até mesmo essa, não conseguimos obter nenhuma informação.
Como sabemos que é uma senha super secreta?
Portanto, esse é um arquivo criptografado,
mas agora queremos pegar esse arquivo binário criptografado e descriptografá-lo.
Portanto, para isso, vamos executar um comando de descriptografia KMS.
Então, desta vez, passamos o arquivo que foi criptografado.
Portanto, é aqui que passamos o arquivo.
Em seguida, consultamos o valor do texto
simples, ou seja, o valor descriptografado,
e gravamos isso em outro arquivo
que será criptografado na base 64, e especificamos a
região.
Então vamos em frente.
O KMS sabe automaticamente qual chave
usar para a descrição porque ela
está incluída no blob do valor criptografado.
Então, deixe-me inserir isso, e isso foi bem-sucedido.
Então, agora, se eu for ao meu arquivo de exemplo descriptografado na base
64, ele estará aqui, é uma coisa muito mais curta,
e agora vamos decodificá-lo na base 64 para
obter o valor do texto.
Portanto, teremos um comando diferente novamente,
se você estiver no Windows ou no Mac,
ou seja, se eu estiver no Mac, usarei este.
Então, estou copiando esse comando, colando-o, e agora fizemos
uma decodificação de base 64 do nosso arquivo.
Portanto, se voltarmos ao Exemplo de arquivo descriptografado. txt, recuperamos nossa
senha super secreta.
Portanto, mostramos a criptografia
e sua operação inversa, a descriptografia.
Obviamente, esses são comandos
de baixo nível, o SDK abstrairá parte disso para nós,
mas isso mostra o exemplo completo
de como você pode usar o comando de criptografia e descriptografia
do KMS com sua própria chave mestra do cliente.
Então é isso, super simples.
Espero que tenha sido útil
e nos veremos na próxima palestra.
