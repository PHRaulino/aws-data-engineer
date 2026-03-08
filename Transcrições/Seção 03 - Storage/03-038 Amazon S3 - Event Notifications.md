Agora, vamos falar sobre as notificações de eventos do S3.
ocorram no Amazon S3.
O que são eventos?
Bem, eventos são coisas como a criação de um objeto, a remoção
de um objeto, a restauração de um objeto ou a ocorrência
de uma replicação.
E você pode filtrar esses eventos.
Portanto, você pode dizer que só quero considerar os
objetos que terminam com JPEG.
Portanto, o caso de uso do Event Notification será, por exemplo,
reagir automaticamente a determinados eventos
que ocorrem no Amazon S3.
Por exemplo, você deseja gerar miniaturas
de todas as imagens carregadas no Amazon S3.
Portanto, você criará sua Event Notification.
E então você pode enviá-lo para alguns destinos.
Pode ser um tópico SNS, pode ser uma fila SQS e uma
função Lambda.
E não se preocupe se você ainda não sabe disso,
pois aprenderemos sobre esses recursos nas próximas palestras.
Portanto, você pode criar quantos eventos S3 desejar e
pode enviá-los para qualquer destino que desejar.
Portanto, a ideia é que esses eventos
sejam normalmente entregues em segundos
a esses destinos, mas às
vezes pode levar um minuto ou mais.
Agora, para que as notificações de eventos funcionem,
precisamos ter permissões de IAM.
Portanto, o serviço S3 está enviando dados para
um tópico do SNS, por exemplo.
Portanto, para que isso seja possível, precisamos anexar
o que chamamos de política de acesso a recursos do SNS.
Essa é uma política de IAM que você anexa ao tópico do SNS
e que permitirá que o bucket do S3 envie
mensagens diretamente para o tópico do SNS.
Da mesma forma, se usarmos o SQS,
criaremos uma política de acesso a recursos do SQS,
que autoriza o serviço S3 a enviar dados para a nossa
fila do SQS.
E, finalmente, para a função Lambda, você já deve
ter adivinhado, precisamos de uma política
de recursos Lambda anexada à nossa
função Lambda para garantir que o
Amazon S3 tenha o direito de invocar nossa função.
Portanto, aqui não usamos funções de IAM para o Amazon S3.
Em vez disso, definimos políticas de acesso a recursos
no tópico do SNS, na fila do SQS ou na função
Lambda.
E eles funcionam de forma semelhante
ao que tínhamos quando estávamos usando uma política de bucket S3.
Portanto, você precisa se lembrar da função SNS, SQS e lambda como
alvos de notificações de eventos.
Mas agora há uma quarta integração
sobre a qual você também precisa aprender.
Portanto, seus eventos estão indo para seus buckets do Amazon S3.
E todos os eventos acabam no Amazon Event Bridge, não importa o
que aconteça.
Então, todos eles, certo?
E, a partir do Event Bridge, que você ainda não conhece, mas
pode configurar regras.
E a partir do Event
Bridge, você pode, graças a essas regras, enviar
esses eventos para mais de 18 serviços diferentes da AWS como destinos.
Portanto, ele realmente aprimora a capacidade
da S3 Event Notification.
E, novamente, veremos o Event Bridge mais adiante neste
curso, mas com o Event Bridge,
você tem opções avançadas de filtragem muito
mais do que as que tínhamos antes.
Assim, você pode filtrar por metadados, objeto, tamanho e nome.
Você pode enviar para vários destinos ao mesmo tempo.
Você pode dizer, por exemplo, para Step Functions,
Kinesis Data Streams ou Firehose, ou até
mesmo obter os recursos vindos diretamente
do Amazon Event Bridge.
Assim, você pode arquivar eventos, reproduzir
eventos e obter uma entrega mais confiável.
Ok, há muita coisa que você não sabe nesta palestra sobre os serviços
de notícias, mas vamos nos
concentrar apenas no Amazon S3 Event Notifications.
A ideia é que você possa reagir a eventos
que ocorrem no Amazon S3, graças
ao envio para SQS, SNS, Lambda ou Amazon Event
Bridge.
Ok, é isso.
Eu o verei na próxima palestra.
