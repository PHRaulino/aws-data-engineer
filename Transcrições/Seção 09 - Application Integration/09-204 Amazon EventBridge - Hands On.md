Então, vamos dar uma olhada
no
Você pode criar uma regra com um padrão de
evento.
Vamos fazer isso agora mesmo.
Em seguida, você pode ter uma regra de
programação,
que é a maneira antiga de fazer a
programação.
Portanto, agora existe algo chamado
EventBridge schedule.
Também vamos dar uma olhada nisso.
O Pipe consiste em enviar dados de uma
origem de
evento para o destino com filtragem e
enriquecimento opcionais.
E o registro de esquemas é para
examinar os esquemas de todos esses
eventos.
Então, para começar, vamos usar a primeira
opção,
a regra EventBridge com padrão de evento.
Portanto, precisamos criar uma regra, e o
que
queremos fazer é reagir a qualquer evento
em
que uma instância será encerrada ou
fechada.
Então, clique aqui em Service Events
(Eventos de serviço)
e você terá uma lista de todos os eventos
que podem ocorrer em suas contas por
serviço.
Portanto, é muito.
Por exemplo, se você pegar qualquer um
desses,
por exemplo, se você pegar o Lambda,
poderá
dar uma olhada em todas essas coisas.
Ações do console ou EC2, você pode
dar uma olhada em todas essas coisas.
Portanto, há muito mais tipos de coisas
que você pode escolher para eventos.
Portanto, a que vamos examinar
é uma das mais populares.
Ele é chamado de Notificação de alteração
de estado da instância do EC2.
Isso significa que sempre que o
estado de uma instância do EC2
for alterado, receberemos uma notificação.
Portanto, se analisarmos esse evento,
poderemos dar
uma olhada no esquema do evento e,
em seguida, em um exemplo de evento.
Como ele pode se parecer.
Portanto, o esquema define a aparência do
evento de amostra.
E agora queremos poder filtrar esse
evento e o valor do estado.
Portanto, o estado é uma cadeia de
caracteres e temos que sair do valor.
Portanto, podemos dizer Equal, por
exemplo, e teremos vários valores.
Portanto, o primeiro está sendo fechado
e o segundo será encerrado.
Como eu sei disso? Bem, é pelo próprio
esquema.
Se você der uma olhada no padrão de
eventos na
linha inferior, na página inferior,
desculpe, você pode dar
uma olhada nos eventos de amostra 1, 2, 3.
E se você observar o número
5, ele diz "state" (estado):
"shutting-down".
E o número 6 diz "estado": "terminado".
Portanto, esses são os eventos que
queremos capturar.
Portanto, agora nosso filtro de padrão de
evento
está definido bem aqui, no lado direito.
Portanto, agora temos todos os eventos.
E agora, com relação ao alvo, novamente,
temos várias opções.
Assim, podemos dar uma olhada em todas as
opções
aqui, como gateway de API, trabalhos em
lote.
Também podemos reiniciar uma instância do
EC2, encerrar uma.
Temos tópicos SNS, filas SQS, enfim,
muitos.
Mas o que queremos fazer agora é receber
um alerta, então escolhemos SNS Topic e
queremos que seja nosso tópico de
demonstração.
Portanto, crie-o se você não tiver um
tópico.
Você pode simplesmente criar um tópico do
SNS com muita facilidade.
Em seguida, precisaremos ter uma função de
exceção
para podermos enviar uma mensagem para
esse tópico.
Portanto, uma função será criada
automaticamente para nós.
e, em seguida, obtemos mais informações
sobre a política
de novas tentativas e a fila de cartas
mortas.
Então, estamos prontos para começar. Vamos
clicar em Criar.
Vou chamá-lo de
NotifyEC2InstanceShutdownOrTerminated e
clicaremos
em Create.
Portanto, agora que essa função
foi criada, sempre que fecharmos
ou encerrarmos uma instância do
EC2, receberemos uma notificação.
A outra opção é usar o Schedule.
Portanto, no lado esquerdo, você tem
programações
e, em seguida, pode criar uma programação.
E este vai se chamar
InvokeLambdaEveryHour.
E várias opções.
Pode ser uma programação única, em que
fazemos
algo uma vez e depois terminamos, ou
recorrente.
E temos uma programação baseada em Cron ou
uma programação de tarifas.
Usaremos 1 hora e nenhuma
janela de tempo flexível.
E a seguir.
E aqui temos a opção de invocar várias
coisas.
Então, o que queremos fazer a cada
hora? Bem, temos todas essas opções, como,
por exemplo, executar uma tarefa no Amazon
ECS ou colocar um registro no Kinesis
Data Firehose ou invocar uma função
Lambda.
Portanto, você pode dizer, por
exemplo, na função Invoke Lambda
e, se tiver uma função
Lambda, poderá selecioná-la aqui.
Então você entendeu a ideia.
Depois de fazer isso, você terá
um cronograma no Amazon EventBridge.
Outros aspectos que devem ser observados
são os ônibus para eventos.
Portanto, neste momento, temos o
barramento de eventos padrão.
E o barramento de eventos padrão é
qualquer coisa
que seja do tipo de eventos gerados pela
AWS.
Mas você pode criar seu próprio barramento
de eventos,
e este será um barramento de eventos
personalizado.
E aqui você tem a capacidade de
enviar seus próprios eventos para esse
barramento
de eventos e, portanto, pode desenvolver
aplicativos personalizados baseados no
Amazon EventBridge,
o que pode ser muito útil.
Você tem a opção de arquivar seus eventos.
Quando eles acontecem no barramento de
eventos, você
tem um arquivo que pode ser consultado.
E você também pode reproduzir eventos se
quiser
reproduzir um evento passado de um
arquivo.
Certo, outras coisas que você precisa
observar
são as fontes de eventos de parceiros.
Portanto, é possível obter dados
de parceiros terceirizados diretamente em
suas contas do AWS.
Portanto, se você usar, por exemplo, o
Auth0, os eventos do Auth0 serão
colocados e inseridos no Amazon
EventBridge.
E então você pode, por exemplo, usar uma
função Lambda ou
fazer algo depois que alguém tiver feito o
login do zero.
Mas você pode ver que há
muitos tipos diferentes de parceiros aqui.
E destinos de API.
Isso significa que, por exemplo, se você
quiser ter um evento no EventBridge, mas
depois se conectar a um destino HTP
externo, também poderá definir um aqui.
E isso permite que você conecte o
EventBridge a uma fonte externa, por
exemplo,
para ter integração com sua própria
infraestrutura.
Portanto, são muitas coisas diferentes.
E, finalmente, para esquemas, são todos os
esquemas de
todos os eventos do AWS que você tem.
Ou você pode ter seu próprio
registro personalizado para seus próprios
eventos.
Mas isso permite que você entenda a forma
e
o formato que os eventos terão no Amazon
EventBridge.
E é isso. Espero que você tenha gostado.
Você pode acessar aqui as regras
e também desativá-las, se quiser.
Mas espero que você tenha gostado desta
palestra e nos veremos na próxima.
