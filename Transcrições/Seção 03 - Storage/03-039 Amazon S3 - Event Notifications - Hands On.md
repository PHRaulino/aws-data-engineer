Certo, então
Para isso, vou criar um balde.
Eu o chamo de "stephane-v3-events-notifications" e, quando
a Irlanda está...
e vou criar meu balde completamente.
Está bem. Portanto, agora o bucket foi criado.
Vou me aprofundar no assunto.
E o que vou fazer agora é garantir
que as notificações de eventos estejam configuradas.
Então, vou para propriedades,
rolo a tela para baixo e aqui temos notificações de eventos.
E, como você pode ver, temos duas opções.
O número um é criar uma notificação
de evento, e mostrarei isso em um segundo,
ou o número dois é ativar a integração
do Amazon EventBridge para enviar todos
os eventos desse bucket S3
para o EventBridge.
Para isso, basta ligá-lo e você estará
pronto para começar.
Portanto, se eu quisesse, poderia usar o Amazon EventBridge
para capturar os eventos
que ocorrem em meus buckets S3.
Mas vou lhe mostrar a maneira
mais simples, porque é um pouco mais complicada,
que é simplesmente criar uma notificação de evento e
enviá-la, por exemplo, para o SQS.
Portanto, chamarei este de "DemoEventNotification" e, em
seguida, poderemos definir um prefixo, um sufixo,
mas não farei isso.
Em seguida, escolhemos os tipos de eventos.
Portanto, queremos reagir a todos os eventos de criação de objetos.
Isso significa que, sempre que um objeto for
criado, um evento será criado.
Mas, se você quiser, poderá ser mais detalhado
e selecionar os tipos de eventos que deseja.
Mas, para simplificar, vou falar sobre isso aqui.
E você também pode incluir, por exemplo,
remoções de objetos, restaurações de objetos,
e ele mostra todos os eventos que você pode capturar
no lado direito.
Portanto, vou simplificar.
Vou rolar a tela para baixo,
mas, como você pode
ver, há muitos eventos
diferentes aos quais você pode reagir no Amazon S3.
E então, você deseja publicar em um destino.
Portanto, temos três opções.
Temos funções Lambda, tópico SNS e fila SQS.
Vou escolher a fila SQS, mas
primeiro precisamos criar uma fila e, em
seguida, autorizar o Amazon S3
a publicar mensagens nesse destino.
Portanto, o
que vou fazer agora é acessar o Amazon SQS e criar uma fila.
E eu o chamo de "DemoS3Notification. Vou criar essa
fila.
E ele foi criado.
Portanto, o que quero fazer agora é aprimorar a política
de acesso para permitir que meu bucket do S3 grave na minha fila do SQS.
Então, para isso, vou primeiro demonstrar o problema.
Portanto, se eu voltar
aqui e atualizar a página, verei minha fila aparecer.
Então, eu o atualizo e digo DemoS3Events.
Todos os objetos criados e, em seguida,
role a tela para baixo e escolha a fila SQS.
Posso escolher o ARN da fila.
Desculpe. Eu poderia escolher a fila aqui
no menu suspenso, DemoS3Notification.
E se eu tentar salvar minhas
alterações, recebo um erro desconhecido,
que diz: "Ei, você não pode validar a configuração
de destino porque essa fila
do SQS ainda não aceita mensagens dos meus buckets
do S3. Portanto, preciso alterar a política de
acesso clicando em edições, rolando
para baixo, e aqui está
minha política de acesso.
E eu preciso ir em frente e gerar uma nova política.
Então, vou para o Gerador de políticas.
Será uma política de fila do SQS.
E o efeito é permitir que qualquer pessoa, só para ser
bem permissivo, envie uma mensagem.
E o nome do meu recurso na Amazon está bem aqui.
Preciso copiá-lo e colá-lo.
Eu adiciono uma declaração e, em seguida, gero essa política.
E agora, esta é a política que quero usar
para permitir que qualquer pessoa escreva na minha fila do SQS.
Portanto, é muito, muito permissivo, mas funcionará.
Vamos salvar isso.
E agora minha política de acesso foi atualizada.
Portanto, agora, se eu voltar aqui e tentar salvar minhas alterações,
como você pode ver, a operação foi concluída com êxito.
E o que aconteceu foi que, se eu entrasse na minha
fila do SQS e clicasse em enviar e receber mensagens
e, em seguida, clicasse em pesquisar mensagens,
como você pode ver, uma mensagem estava sendo enviada pelo Amazon
S3 para testar o evento, para testar a conectividade.
Portanto, o que posso fazer é pegar essa mensagem e excluí-la.
Portanto, agora queremos testar
se a S3 Event Notification está funcionando ou não com o SQS.
Portanto, vamos fazer upload de um objeto, clicar
em adicionar arquivos e escolher nosso café, o JPEG.
Farei o upload desse arquivo.
Agora o arquivo foi carregado.
E se eu entrar no meu
balde, posso ver que meu café, o JPEG, foi criado.
E imagine que quiséssemos automatizar
isso e criar uma miniatura a partir dela.
Em seguida, precisaremos colocar uma mensagem em nossa fila
do SQS para processá-la e criar uma miniatura.
Portanto, vou optar por mensagens.
E, como você pode ver, uma mensagem foi criada aqui.
E se você observar a mensagem
em si, e vou tentar aumentar o tamanho da
janela, podemos ver o fato de que
o "eventName" era "ObjectCreatedPut".
E se olharmos mais a fundo,
veremos que a chave dessa mensagem é o café,
o JPEG.
Assim, o café, o JPEG, foi criado
e gerou um evento inteiro em minha fila do SQS.
Portanto, isso mostra
o poder das S3 Event Notifications.
O que posso fazer aqui é excluir a mensagem
e pronto.
Está bem. Então é isso.
Já vimos as notificações de eventos do S3.
O que você precisa lembrar
novamente é que pode enviar para SQS, SNS e Lambda, bem como
enviar todos os eventos para o Amazon EventBridge
para processamento adicional e envio para mais destinos.
Está bem. É isso aí.
Eu o verei na próxima palestra.
