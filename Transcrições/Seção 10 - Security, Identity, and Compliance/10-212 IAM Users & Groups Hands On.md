Então,
Portanto, na barra
de pesquisa, digito IAM e vou para o console do IAM.
Portanto, ao chegar ao IAM Dashboard, temos algumas
recomendações de segurança com
as quais não podemos nos preocupar por enquanto.
E quero chamar sua atenção para
o fato de que, no lado esquerdo, vamos para os usuários.
Portanto, é aqui que estamos criando usuários para o IAM, mas, primeiro,
vamos observar algo.
Se você for ao canto superior direito e clicar em Global,
verá que a seleção de região não está ativa.
Isso significa que o IAM, como um serviço completo, é um serviço global e,
portanto, não há nenhuma região a ser selecionada.
Quando você criar um usuário no IAM, ele estará disponível
em todos os lugares, mas alguns outros consoles
que veremos neste curso serão específicos para cada
região.
Portanto, é apenas algo a ser observado.
Agora temos usuários, e por que criamos usuários?
Bem, criamos usuários porque,
no momento, estamos usando o que chamamos de usuário raiz.
Portanto, se você clicar
aqui, verá que há apenas o ID da conta disponível para você.
Portanto, quando isso acontece,
significa que você está usando
a conta raiz e não é uma prática recomendada usar a conta raiz.
Portanto, queremos criar usuários, como os usuários administradores,
que nos permitirão usar nossas contas com mais segurança.
Portanto, para isso, vamos criar um usuário
e fornecerei um nome de usuário, por exemplo, Stephane.
Portanto, é claro que quero fornecer a mim mesmo acesso
ao console de gerenciamento,
então vou fazer isso e temos
a opção de usar o centro de identidade, o que é
recomendado, ou criar um usuário
IAM.
Escolherei a segunda opção porque ela é mais
simples e, do ponto de vista do exame, é a
que você precisa conhecer.
Mas não se preocupe,
isso não afeta o andamento de seu curso.
Pronto, criamos um usuário IAM
e agora temos que definir a senha.
Portanto, se esse fosse um usuário que não fosse
eu, eu deixaria como senha gerada automaticamente
e deixaria isso para que o
usuário alterasse essa senha no próximo login, mas como
sou eu, vou inserir uma
senha personalizada e vou desmarcar
isso porque não preciso alterar minha senha no próximo login.
Então, vamos clicar em next.
Em seguida, temos que adicionar permissões a esse usuário, portanto,
podemos adicioná-lo diretamente ou começar com grupos.
Então, vamos criar um grupo e vamos criar um grupo.
O nome do grupo será admin e o nome
da política será acesso de administrador.
Portanto, agora que isso foi feito, podemos
adicionar o usuário ao grupo de administradores.
Então, vamos clicar em next
e podemos revisar tudo agora mesmo.
Portanto, temos o nome de usuário, as permissões no
grupo e temos tags, e as tags estão em toda parte na AWS.
Eles são opcionais, mas permitem que você forneça metadados
a muitos de seus recursos.
Por exemplo, eu poderia dizer
que o departamento de Stephane é engenharia.
Isso não é algo que farei em todo
o curso, mas quero mostrar
uma vez como você pode adicionar
tags a recursos no AWS.
Pronto, agora o usuário foi criado com sucesso.
Portanto, agora podemos enviar instruções de assinatura por e-mail ou baixar
arquivos CSV e, em seguida, fazer login com esse usuário.
Mas, primeiro, vamos voltar à lista de
usuários e dar uma olhada em tudo.
Portanto, aqui estão minhas listas de usuários, aqui
estou eu e também temos grupos.
Portanto, se eu for para o lado esquerdo, grupos de usuários,
temos administradores.
Então, vamos observar os administradores.
Portanto, o admins tem um usuário chamado Stephane.
E se você observar as permissões dos administradores,
verá que há acesso de administrador associado ao grupo
de administradores.
Agora, se eu for ao meu usuário, Stephane, podemos
examinar as políticas de permissão e ver
que ele também tem acesso administrativo,
mas esse não foi anexado diretamente.
Ele foi anexado por meio do administrador do grupo.
Isso significa que Stephane herdou todas as permissões do
administrador do grupo em que está.
E é por isso que colocamos os usuários em grupos.
É um pouco mais simples gerenciar as permissões dessa forma.
Então, agora vamos voltar ao nosso
painel e entrar com o nosso usuário, Stephane.
Então, primeiro, o que podemos fazer é examinar nossas
contas do AWS, que têm um ID de conta e um URL de login.
Agora você pode personalizar esse URL de login com muita facilidade,
criando o que é chamado de alias de conta.
Portanto, poderia ser aws-stephane-v3 e, em seguida, Create alias, ou seja, qualquer alias
até que alguém não o tenha criado, portanto, ele precisa ser
exclusivo.
Por exemplo, a v5 está disponível.
Portanto, agora o uso desse alias pode simplificar meu URL de assinatura.
Agora, para fazer login usando minhas contas
Stephane, podemos usar o mesmo navegador
ou criar uma nova janela do navegador no modo privado.
E a vantagem de fazer isso
é que podemos ter duas janelas lado a lado usando o AWS.
Portanto, se você não fizer isso, tudo bem, mas se fizer login usando
a conta Stephane na janela do lado direito, você será desconectado
no lado esquerdo, essa é a única diferença.
Portanto, para usar duas contas ao
mesmo tempo, a rota à esquerda e a minha conta à direita,
o que estou fazendo como truque é usar uma janela privada
no meu navegador da Web, e o Chrome tem esse recurso, o Firefox tem
esse recurso, o Safari tem esse recurso e assim por diante.
Portanto, ao colar o URL de assinatura, como
você pode ver, obtenho o login e como usuário do
IAM e, para acessar essa página, podemos voltar para uma.
E, como você pode ver, quando você faz um login no AWS,
você tem o login do usuário root ou o login do usuário IAM.
Então, para voltar a isso, vamos para o usuário IAM.
Digitamos o ID da conta ou o alias da conta que posso copiar
aqui e, em seguida, somos levados a esta página.
Portanto, o nome de usuário do IAM será
Stephane e a senha será a que você definiu anteriormente
e, em seguida, você entrará.
Agora, o mais legal é que, se eu olhar para o lado superior
direito, o IAM fez login usando meu usuário IAM.
Portanto, ele diz o ID da conta e o usuário do IAM.
Mas, se eu olhar no canto superior direito,
ele diz apenas o ID da conta, o que
me mostra que são as contas raiz.
Portanto, temos as contas raiz conectadas
no lado esquerdo por meio de uma janela
normal e o usuário IAM conectado no lado direito por meio de
uma janela privada.
Certifique-se de não perder os logins da conta raiz
e o login de administrador.
Caso contrário, você terá sérios problemas com sua conta
e precisará entrar em contato com a AWS para obter suporte.
No momento, não posso ajudá-lo com isso.
Agora, do ponto de vista do curso, recomendo
que você use o usuário IAM e não o usuário raiz, mas essa é apenas uma recomendação
normal.
Às vezes você me verá usando o root, às
vezes estou usando o usuário IAM.
Mas quando for necessário usar raízes ou quando for
necessário usar um usuário IAM, eu informarei no curso.
Não se preocupe com isso.
Agora, para o restante desta
seção, mantenha essas duas janelas abertas e nos veremos
na próxima palestra.
