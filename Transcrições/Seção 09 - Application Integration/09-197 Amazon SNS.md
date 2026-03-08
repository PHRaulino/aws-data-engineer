E se, desta vez, você quiser enviar uma mensagem e ter
muitos, muitos receptores diferentes?
Assim, você poderia ter uma integração direta em que, por exemplo, um aplicativo
de serviço de compras poderia enviar uma notificação por e-mail e, em
seguida, enviar uma mensagem para um serviço de fraude, enviar
uma mensagem para um serviço de remessa e talvez
até mesmo enviar uma mensagem para uma fila SQS.
Isso é complicado porque toda vez que você precisa
adicionar um novo serviço de recebimento.
Você precisa criar e escrever essa integração.
Em vez disso, o que você pode querer fazer
é chamado de Pub/Sub ou Publish-subscribe.
A ideia é que o serviço de compra envie
uma mensagem para um tópico do SNS que esteja
publicando uma mensagem em um tópico.
E esse tópico terá muitos assinantes.
E cada assinante poderá receber
essa mensagem do tópico do SNS
e tê-la como sua.
Portanto, esse é outro tipo de padrão
chamado de padrão Pub/Sub.
Portanto, no
Amazon SNS, o produtor de eventos só envia mensagens
para um tópico específico do SNS.
E os receptores de eventos ou as assinaturas
querem ouvir as notificações de tópicos do SNS.
Portanto, cada assinante do seu tópico do SNS receberá
todas as mensagens enviadas para o tópico, exceto se você
estiver usando um recurso para
filtrar mensagens, o que também é possível.
Então, quantos assinantes você pode obter por tópico?
Bem, você pode ter até 12.000.000 de assinaturas por tópico,
ou seja, bastante.
E o número pode mudar com o tempo.
Ele não atualizará esse slide.
Isso serve apenas para lhe dar uma visão geral de quantos
assinantes você pode obter.
E em sua conta, você pode ter até 100.000 tópicos e também pode aumentar
esse limite.
E isso pode mudar, mas, novamente, apenas
para lhe dar uma ideia de qual pode ser o limite, mas
você nunca é testado quanto aos limites em si para o SNS.
Portanto, para o SNS, você publicará seus assinantes
e o que eles podem ser?
Bem, você pode enviar e-mails diretamente do SNS.
Você pode enviar SMS e notificações móveis.
Você também pode enviar dados diretamente para pontos de extremidade
HTTP ou HTTP(S) especificados, mas
o SNS também tem integrações com serviços específicos da AWS, como o SQS,
para enviar sua mensagem
diretamente para uma fila, para o Lambda, para que uma função
execute algum código depois que a mensagem for recebida, ou para o Kinesis
Data Firehose para enviar dados, por exemplo,
para o Amazons free ou Redshift.
Além disso, o SNS recebe dados
de vários serviços da AWS.
Assim, eles enviam diretamente para o SNS, podendo
ser alarmes do CloudWatch, notificações
do Auto Scaling Group, alterações
de estado do CloudFormation, buckets S3 de orçamentos,
eventos do DMS, Lambda, DynamoDB, RDS e assim por diante.
Assim, você não precisa se lembrar delas.
Porém, assim que houver
algum tipo de notificação no AWS, os serviços
enviarão uma notificação para
um tópico especificado do SNS.
Agora, SNS, como isso funciona?
Para publicar uma mensagem
no SNS, você usa o tópico, publicar SDK.
Assim, você cria um tópico.
Em seguida, você cria assinaturas
ou muitas assinaturas que publica
no tópico do SNS e pronto.
Todos os assinantes receberão
automaticamente essa mensagem.
Ou há algo chamado publicação
direta para aplicativos móveis,
SDK, e você precisa criar um aplicativo
de plataforma, um endpoint
de plataforma e publicar no endpoint de plataforma,
e isso funciona em termos de assinantes para o Google GCM, Apple APNS ou Amazon
ADM, que são maneiras diferentes de seu aplicativo móvel
receber notificações.
Em termos de segurança, o Amazon
SNS tem o mesmo tipo de segurança que o SQS, portanto, ele tem criptografia
em voo por padrão, criptografia em repouso
usando chaves KMS e criptografia do lado do cliente
se o seu cliente quiser enviar alguma
mensagem criptografada para o SNS, mas, novamente, cabe ao seu cliente a responsabilidade
de fazer a criptografia e a descriptografia.
Em termos de controles de acesso,
as políticas de IAM estarão no centro da segurança
porque todas as APIs do SNS serão reguladas pelas políticas
de IAM.
E você pode definir políticas de acesso ao SNS que
são muito semelhantes às políticas de bucket
do S3, e elas são muito úteis quando
você deseja ter acesso entre contas aos
tópicos do SNS ou permitir que outros
serviços, como os eventos
do S3, gravem nos tópicos do SNS.
Então é isso, espero que tenham gostado
e vejo vocês na próxima palestra.
