Então, vou clicar no meu nome de usuário, Stephane,
e vou para Credenciais de segurança.
Vou rolar a tela para baixo e criar uma chave de acesso.
Como você pode ver, há
algumas seleções que precisam ser feitas e, com
base na seleção que estou fazendo,
por exemplo, quero uma chave de acesso para a
CLI, o AWS terá uma alternativa recomendada.
Por exemplo, para a CLI, é melhor
usar o CloudShell, que mostrarei
na próxima aula, portanto, não se
preocupe com isso.
Ou usar a CLI V2 e uma autenticação por meio do IAM Identity
Center, que não mostrarei a você
porque é um pouco
mais complicado.
Portanto, com base no que você deseja
fazer, se for um aplicativo de código local executado fora do
AWS ou no AWS e assim por diante, você terá
algumas recomendações na parte inferior.
Por enquanto, usaremos a CLI
e usaremos essas chaves de acesso e clicaremos
aqui para dizer "Entendo
a recomendação acima", e ainda quero criar
uma chave de acesso porque é importante
que você entenda como elas são, como
funcionam, o que são e assim por diante.
Então, vamos criar essa chave de acesso.
E agora, este é o único momento
em que você poderá ter acesso à chave de acesso e
à chave de acesso secreta.
Portanto, voltarei agora para uma
versão anterior dessa palestra, na qual você
verá a IU antiga, mas não se
preocupe, nada muda a partir desse ponto.
A primeira coisa que preciso fazer é configurar minha CLI do AWS.
Então, vou digitar: aws configure.
Em seguida, sou convidado a inserir meu ID de chave de acesso.
Muito bom, posso simplesmente digitar este e pressionar Enter.
E, em seguida, sou convidado a digitar minha chave de acesso
secreta, que também digitarei aqui.
O nome padrão da região,
portanto, essa é uma região próxima a você.
Escolherei eu-west-1 porque farei
todos os meus tutoriais eu-west-1, mas você escolherá sua
própria região e poderá inserir
seu próprio nome de região.
O nome da região, a propósito, pode ser obtido diretamente
neste menu suspenso aqui.
Ele mostra o nome da região, bem
como o código da região.
Então, para mim, vou usar meu eu-west-1.
Pressionarei Enter e, no formato de saída padrão,
também pressionarei Enter.
Portanto, agora minha CLI do AWS está configurada e podemos
dar uma olhada em como ela funciona.
Podemos usar: aws iam list-users e pressionar
Enter.
E isso listará todos os usuários da minha conta.
E, como podemos ver, o
usuário que tenho agora se chama Stephane,
aqui está o UserId, aqui está o ARN, quando ele
foi criado e quando
a senha foi usada pela última vez.
O que é muito semelhante ao que eu obteria
se entrasse nesta interface do usuário aqui.
Portanto, o Console de gerenciamento e
a CLI fornecem informações semelhantes.
Em seguida, quero mostrar o que acontece
se removermos as permissões dos nossos usuários.
Portanto, vou até admins e removerei
o usuário Stephane do grupo de administradores.
Então, novamente, se eu voltar ao meu usuário, Stephane, ele não tem
nenhuma permissão.
E eu fiz isso, obviamente, com minha conta root,
não com as outras contas.
Portanto, agora, se eu entrar em minha interface do
usuário e, obviamente, atualizar essa página,
receberei um erro dizendo que, sim, não
tenho as permissões para fazer isso.
Mas vamos tentar fazer a mesma coisa com a CLI.
Portanto, vamos fazer uma chamada "iam list-user" e não obteremos
resposta porque, na verdade, ela estava sendo negada.
Portanto, as permissões da CLI obviamente
serão exatamente as mesmas que as permissões
obtidas no console do IAM.
Portanto, a conclusão desta
palestra é que você pode acessar o AWS usando o Console de gerenciamento
ou usando a chave de acesso e a chave de acesso secreta
que você pode configurar e usar na CLI.
Espero que tenham gostado
e nos veremos na próxima palestra.
E, obviamente, não se esqueça
de adicionar seu usuário de volta ao grupo, caso contrário,
isso seria horrível.
Então, vou acessar Grupos, administradores, e adicionarei
o usuário Stephane de volta ao meu grupo, e agora sou um administrador
novamente.
Então é isso, vejo vocês na próxima palestra.
