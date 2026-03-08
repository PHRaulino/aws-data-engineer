Agora, vamos dar
Então, antes de tudo, vamos falar sobre os usuários.
E, como você pode ver, o usuário
Stephane faz parte do grupo de administradores
e, portanto, tem permissões de acesso de administrador ao AWS.
Isso significa que, se eu usar meu usuário Stephane para
entrar no console do IAM, agora estou usando meu usuário e, em seguida, vou
para o lado esquerdo e clico em usuários, como
você pode ver, posso ver meu usuário Stephane, que está
bem aqui.
Portanto, meu usuário Stephane tem permissão para fazer qualquer
coisa porque é um administrador.
Mas o que vou fazer é acessar os grupos
de administradores e remover meu usuário Stephane
desse grupo.
Portanto, ao remover o usuário, o que eu fiz agora,
Stephane perde suas permissões no lado direito.
Como podemos ter certeza disso?
Bem, vamos atualizar esta página.
E, como você pode ver, agora não vejo nenhum usuário e recebo
uma mensagem de acesso negado, dizendo
que não tenho permissão para fazer iamListUsers.
Portanto, como removi meu usuário Stephane do grupo
de administradores, perdi as permissões para ver os usuários
no lado direito.
Portanto, vamos tentar corrigir isso.
Então, vamos acessar o IAM e,
em usuários, encontraremos Stephane aqui.
E, neste momento, como
você pode ver, Stephane não tem nenhuma política de permissão,
mas vamos adicionar permissões.
Portanto, podemos adicionar permissões
diretamente ou criar uma política em linha.
Então, vamos adicionar permissões, e isso será mais fácil.
E assim, novamente, poderíamos adicionar o usuário de volta a um grupo.
Não é isso que queremos.
Ou podemos anexar políticas diretamente ao meu usuário.
Portanto, a política que vou anexar será
a IAMReadOnlyAccess.
Portanto, isso permitirá que meu usuário Stephane
leia qualquer coisa no IAM, que é o que queremos.
Então, vamos adicionar essa permissão
e agora essa política foi adicionada.
Então, voltando aqui, vamos atualizar a página.
E, como você pode ver agora, posso finalmente fazer minha chamada
à API novamente e ver o usuário Stephane na minha categoria de usuários.
Assim, posso ver os usuários, posso ver os grupos de usuários, como admin,
mas posso criar um grupo?
Vamos tentar criar o grupo de desenvolvedores
e, em seguida, criar esse grupo.
E, como você pode ver, não posso criá-lo porque
não tenho permissão para criar um grupo.
Recebi apenas o acesso somente leitura no IAM.
Portanto, como tenho acesso somente
de leitura, não posso criar grupos.
Isso mostra que você só pode permitir que os usuários façam o que
devem fazer.
E, é claro, se eu quiser dar acesso para criar grupos
no lado direito,
precisarei anexar um conjunto de permissões maior,
como o acesso total do IAM.
Então, a seguir, vamos fazer algo.
Em seguida, vou para o lado esquerdo,
em grupos de usuários, e vou criar um grupo.
Portanto, esse grupo será chamado de desenvolvedores.
Em seguida, adicionarei o usuário Stephane a esse grupo e anexarei
qualquer política que encontrar, por exemplo,
AlexaForBusiness, mas isso não importa.
Basta anexar a primeira política que você puder e
vamos criar esse grupo.
Ok, então isso foi adicionado.
E, por fim, vamos entrar no grupo de administradores.
E, novamente, vamos adicionar
usuários e adicionar novamente Stephane a esse grupo.
Agora, se voltarmos ao usuário Stephane, vamos acessar
o IAM, ver os usuários e ver Stephane, vou encerrar essa mensagem
no lado direito.
Portanto, se considerarmos Stephane como o usuário, como podemos
ver, temos três políticas de permissão anexadas ao meu usuário.
Temos o acesso de administrador que foi herdado do
administrador do grupo.
Temos essa política gerenciada AlexaForBusiness que
foi anexada por meio dos desenvolvedores de grupo.
E, por fim, o IAMReadOnlyAccess que
foi anexado diretamente.
E, como você pode
ver, herdei permissões diferentes
com base na forma como foi anexado.
Agora, vamos examinar as políticas em detalhes.
Portanto, no lado esquerdo, vamos dar uma olhada nas políticas.
Primeiro, vamos dar uma
olhada na política AdministratorAccess.
Portanto, se olharmos para ela, é a permissão
que nos deu acesso de administrador a tudo.
E se você observar as permissões
definidas nessa política como um resumo, como pode ver,
isso permite todos os serviços na AWS.
E esse número pode mudar com o tempo.
Não importa.
O curso será atualizado.
Portanto, todos esses serviços, por exemplo, o App Mesh,
o Alexa for Business ou o Amplify, têm acesso total.
Então, como essa permissão é definida?
Bem, se você clicar em JSON,
este é o formulário JSON dessa política, e podemos
ver que aqui temos allow Action, star e resource, star.
Portanto, estrela na AWS significa qualquer coisa.
Isso significa que permitimos qualquer ação em qualquer recurso.
E, é claro, permitir qualquer
ação em qualquer recurso é exatamente a mesma
coisa que conceder acesso de administrador a alguém.
Portanto, é assim que ele foi definido.
Se dermos uma olhada em outra política,
por exemplo, a IAMReadOnlyAccess que vimos anteriormente.
Portanto, se observarmos
isso, veremos que o IAM está autorizado com Full: List e Limited: Read.
E se eu clicar nela, você poderá ver todas
as chamadas de API permitidas como
parte dessa política, o que é muito útil.
Mas se observarmos como isso foi realmente definido,
vamos clicar em JSON.
E aqui temos o documento JSON que mostra como
isso foi definido.
Portanto, o efeito é permitir, e então listamos as chamadas de API que estão
sendo permitidas.
Portanto, temos este, este e o Get*.
Portanto, quando você tem Get*, ele diz que qualquer coisa
que comece com Get e tenha algo depois é autorizada.
Por exemplo, obter usuários ou obter grupos.
O mesmo vale para a lista.
Portanto, temos uma lista*.
Portanto, liste os usuários ou liste os grupos.
Portanto, ao usar
uma estrela, englobamos e agrupamos muitas chamadas de API.
Portanto, tudo isso é permitido no Resource*.
Portanto, isso resume o
que é a política de acesso IAM somente leitura.
Portanto, isso é muito útil.
Você também pode criar sua própria política.
Então, vamos criar uma política
e temos um editor visual ou um editor JSON.
Portanto, se você tiver JSON, poderá simplesmente editá-lo
e criar seu documento JSON com esse construtor,
o que é muito útil.
Ou você pode usar o editor visual.
Por exemplo, digamos que seja o IAM,
queremos criar coisas para o IAM.
E que ação queremos autorizar?
Bem, queremos autorizar o ListUsers.
Então, vamos pegar isso e usar o GetUser.
Portanto, apenas duas chamadas de API.
E, como podemos ver, selecionamos um dos 38
na lista e um dos 32 na leitura.
E então, em que queremos autorizar isso?
Em todos os recursos ou somente em recursos específicos?
Portanto, esse é um exemplo muito simples,
mas, como você pode ver, esse construtor é muito útil.
E quando você clicar em next, poderá
dar uma olhada e dizer MyIAMPermissions.
E então criamos essa política.
E se dermos uma olhada na política que criamos,
podemos dar uma olhada no JSON
correspondente e ver que, de fato, por meio do editor visual,
permitimos iam:ListUsers e iam:getUser no Resource*.
E essa política pode ser anexada a grupos ou
a usuários e assim por diante.
Portanto, é assim que você gerencia as permissões no AWS.
Então, para encerrar essa prática, vamos
aos grupos de usuários
e excluiremos o grupo de desenvolvedores porque não
precisamos dele.
Em seguida, entrarei no meu usuário Stephane
e removerei esse IAMReadOnlyAccess que foi
anexado diretamente.
Portanto, agora Stephane pertence apenas ao grupo admin
e tem acesso de administrador.
Então, é claro, se eu voltar
ao meu console IAM aqui e olhar apenas para os usuários, como você pode ver, sim,
tudo está aparecendo bem.
Portanto, ele está funcionando corretamente.
Muito bem, então é isso para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
