EventBridge, e o Amazon EventBridge costumava ser formalmente
conhecido como CloudWatch Events, portanto, você verá o
EventBridge no exame, mas, para que
você saiba, se você tiver uma experiência antiga com a
AWS, ele costumava ser chamado de CloudWatch Events.
Portanto, com o EventBridge, você pode fazer muitas coisas.
Por exemplo, podemos agendar tarefas cron na nuvem, para
que possamos agendar scripts.
Por exemplo, dizemos: "Ei, a cada hora, acione uma função
Lambda", e essa função Lambda
executará um script.
Portanto, os eventos são gerados a cada
hora, daí o nome Amazon EventBridge,
mas não apenas um cronograma como a cada hora, ele
também pode reagir a um padrão de evento.
Portanto, há regras de eventos que podem reagir
a um serviço que está fazendo algo.
Por exemplo, você pode reagir ao
evento de login do usuário raiz do IAM no console.
Portanto, quando isso acontecer, talvez você queira enviar
uma mensagem para um tópico do SNS e receber uma notificação por e-mail,
de modo que, se alguém estiver usando a conta raiz, você receberá
um e-mail, o que pode ser um bom
recurso de segurança para suas contas.
Além disso, por exemplo, você tem destinos
diferentes, pode acionar
funções Lambda, enviar mensagens
SNS e SQS, e assim por diante.
Assim, o EventBridge fica no meio
e temos todas as fontes que podem enviar eventos para
o Amazon EventBridge.
Assim, por exemplo, as instâncias do EC2 quando são iniciadas, quando
são interrompidas, quando são encerradas e assim por diante.
Code Build, por exemplo,
se você tiver uma compilação que
falhe ou S3, sempre que houver um evento, por
exemplo, quando um objeto for carregado,
ou Trusted Advisor, quando você tiver
uma nova descoberta de segurança
em suas contas ou, como uma boa combinação, você pode combinar o EventBridge
e o CloudTrail e realmente interceptar qualquer chamada de API feita em suas contas
da AWS, o que é enorme.
Além disso, como eu disse, você pode ter uma programação
ou um cron, ou seja, a cada quatro horas ou toda segunda-feira às 8h, a primeira segunda-feira
do mês, isso também é algo que
você pode fazer.
Em seguida, esses eventos são enviados para o Amazon EventBridge
e você pode configurar um filtro.
Por exemplo, você diz: "Ei, eu só quero esses eventos para
um intervalo específico", para a Amazon é grátis, por exemplo.
Em seguida, o EventBridge gerará um documento adjacente
que representa os detalhes de seus eventos.
Portanto, qual instância, por exemplo, é iniciada,
se sua ID e assim por diante.
Muitas informações, o horário, o IP e assim por diante.
Assim, quando isso for feito, esse documento JSON, esse evento, poderá
ser enviado para vários tipos de destinos diferentes, permitindo
que você faça integrações realmente incríveis.
Por exemplo, você pode agendar e acionar uma função Lambda, pode
agendar um lote no AWS Batch, pode iniciar uma tarefa do ECS para
o Amazon ECS, pode enviar uma mensagem para o SQS, para o SNS
ou até mesmo para um Kinesis Data Stream, pode, por
exemplo, iniciar uma Step Function,
pode iniciar um pipeline de CI/CD com o CodePipeline
ou uma compilação com o CodeBuild, portanto, você não sabe
realmente todas essas coisas, é claro, esses são serviços diferentes da AWS, mas estou apenas
dando uma visão geral do que você pode fazer e também pode,
por exemplo, iniciar uma automação do SSM ou uma ação
específica do EC2, como iniciar, parar ou reiniciar uma instância do
EC2.
Assim, você pode ver que as possibilidades são infinitas
e que isso realmente depende do seu caso de uso.
Portanto, o Amazon EventBridge é o que chamamos
de barramento de eventos padrão, que é o que acabamos
de ver, que representa os serviços da AWS que enviam
seus eventos para o barramento de eventos padrão, mas o Amazon EventBridge
tem mais recursos.
Existe algo chamado barramento de eventos de
parceiros, e esse é o AWS que se integrou com parceiros,
provavelmente parceiros de
software como serviço, e eles enviarão seus
eventos diretamente para o barramento de eventos de parceiros.
Portanto, se você estiver usando, por exemplo, Zendesk, Datadog, Auth0 ou
outros, precisará verificar a lista de parceiros.
Então, há uma chance
de que eles possam enviar seus eventos
diretamente para um barramento de eventos de parceiro
especificado e, assim, você pode reagir às mudanças
que acontecem fora da AWS diretamente em suas contas.
E, por fim, há um barramento de eventos personalizado
para que você possa criar seus próprios barramentos
de eventos e, em seguida, seus próprios aplicativos podem enviar seus
próprios eventos para um barramento de eventos personalizado
e, portanto, você tem a mesma capacidade de enviar esses eventos para
destinos diferentes graças às regras do EventBridge.
Além disso, você pode acessar barramentos de eventos, contas cruzadas,
usando políticas baseadas em recursos, como veremos em breve.
Você também pode arquivar eventos, ou seja, todos
eles ou apenas um subconjunto de eventos em
um filtro e, ao arquivar os eventos, você
pode defini-lo como retenção indefinida ou um
período definido para retenção, certo?
O que você pode fazer com isso é reproduzir esses eventos
arquivados.
Por exemplo, digamos que haja um bug na sua função Lambda
e você queira corrigi-lo, então você o corrigiu
e depois quer testar novamente o evento, reproduzi-lo,
então você pode reproduzir esses eventos arquivados,
o que é muito útil para depuração, muito útil
para solução de problemas e também
para corrigir a produção.
Agora, o EventBridge recebe muitos eventos
de diferentes lugares e, portanto, você precisa
entender como os eventos serão e lembre-se
de que esses eventos estão nesse formato adjacente
que acabamos de ver.
Portanto, há um Schema Registry e o recurso
é que o EventBridge analisará os eventos em seu
barramento e, em seguida, inferirá
o esquema, e o esquema do Schema Registry permitirá
que você gere código para seu aplicativo que saberá
antecipadamente como os dados estão estruturados
no barramento de eventos.
Por exemplo, este é um exemplo de
um CodePipeline específico em ação.
Há um esquema e você pode baixar o código
diretamente usando o botão laranja, e ele saberá
diretamente como inferir o esquema e estruturar
os dados do seu barramento de eventos.
Além disso, os esquemas podem ser
versionados para que você possa, com o tempo, iterar entre os esquemas
do seu aplicativo, é claro.
Agora, temos políticas baseadas em recursos para o EventBridge, o que
isso significa?
Isso significa que você pode gerenciar permissões para
um barramento de eventos específico.
Por exemplo, você
pode dizer que um barramento de eventos específico pode
ter permissão ou negar outros eventos de outras regiões ou contas,
e o caso de uso para isso, por exemplo,
seria ter um barramento de eventos central
dentro da sua organização da AWS,
ou seja, um conjunto de contas e todos esses eventos
serão agregados.
Bem, temos um barramento de eventos central com uma conta
específica e vamos adicionar uma política baseada em recursos
específicos, permitindo que outras contas enviem eventos
para ele e, portanto, essa outra conta, por exemplo, poderá
colocar eventos e enviar eventos diretamente
para o barramento de eventos central.
Então é isso, já vimos o EventBridge da esquerda para a direita, você
sabe tudo sobre ele.
Portanto, lembre-se de que você pode reagir a eventos
que ocorrem em suas contas, graças ao barramento
de eventos padrão, mas também a eventos de parceiros e a seus próprios
eventos com barramentos personalizados,
você tem o recurso Schema Registry e, em seguida, tem
políticas baseadas em recursos, que permitem
que você tenha um recurso entre contas, por exemplo, para barramentos de eventos.
Ok, é isso, espero que você tenha gostado
e nos vemos na próxima palestra.
