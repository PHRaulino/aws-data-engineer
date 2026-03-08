Então, você clica em get started (começar),
e isso lhe dá apenas uma página de visão
geral do que você pode fazer com o DMS, mas a verdadeira
mágica acontece no lado esquerdo.
Portanto, isso pode mudar, mas a ideia continua a mesma.
Você pode fazer uma descoberta e uma avaliação
em que criará um coletor de dados, encontrará
bancos de dados, analisará o inventário
e usará as recomendações.
Você pode converter ou mover para gerenciado, portanto,
a ideia é converter um esquema usando
a ferramenta DMS Schema Conversion.
Em seguida, você move seus dados para o AWS e passa
para um serviço gerenciado,
ou pode migrar ou replicar dados.
E aqui, escolhemos os pontos finais. Veremos
isso em um segundo.
Criamos uma instância de provisão
e criamos uma tarefa para a replicação.
Você vê que, para algumas dessas
opções, temos Provisioned ou Serverless
para a migração da replicação.
E aqui, para converter um banco de dados, temos essa conversão
de esquema.
Ou, se não convertermos o esquema, teremos
uma migração de dados homogênea.
Isso é apenas para lhe dar uma visão geral do DMS, mas a verdadeira
mágica acontece no lado esquerdo.
Portanto, aqui você entrará em Endpoints e daremos uma
olhada nele.
Portanto, antes de mais nada, é assim que se movem os dados.
Portanto, pode ser da origem para o destino e,
por isso, você deve criar um ponto
de extremidade para a origem e o destino.
Portanto, a ideia é que eu crie um endpoint, e aqui
você escolhe o que quiser.
Portanto, você insere um identificador e, em seguida,
precisa escolher o mecanismo de origem.
Portanto, você tem todas essas opções para os mecanismos de origem.
Por exemplo, você escolhe o Amazon Aurora MySQL.
Em seguida, você deve inserir
todas as informações sobre o endpoint.
Não podemos fazer isso
porque não temos um banco de dados do Aurora pronto,
mas você entendeu a ideia.
Por fim, você tem a opção de alguns bancos de dados
para testar a conexão do endpoint.
Isso é opcional, mas pelo menos você poderá ver
se a instância de replicação, que criaremos
em um segundo momento,
pode ou não se conectar à sua origem.
Portanto, você tem o mesmo tipo de ideia com o
destino, no qual você diz em que deseja que o DMS escreva.
E, novamente, você precisa escolher um mecanismo de
destino entre a lista.
E você insere algumas configurações.
Por exemplo, se você escolher DynamoDB aqui, insira um acesso
de função de serviço, configuração de endpoint, assistente, editor
e assim por diante e, em seguida,
teste novamente a conexão com o endpoint.
Portanto, você também obtém muitas informações
ao escolher um endpoint no lado direito
sobre o que fazer e as práticas recomendadas.
Assim, depois de criar dois endpoints, você
pode criar uma tarefa de replicação.
Portanto, você tem duas opções.
Para essa tarefa, você pode criar
uma instância de replicação, e aqui você
cria uma instância de replicação
criando de fato um servidor físico.
Portanto, aqui, podemos escolher o tamanho do servidor,
como você pode ver.
Para uma tarefa de replicação maior,
talvez você queira escolher um servidor maior.
E você pode clicar aqui para estimar a classe
de instância e o armazenamento.
E então você pode configurá-lo.
Você diz se quer ou não alta disponibilidade,
o tipo de rede, aplica um
grupo de sub-rede, aplica grupos
de segurança e assim por diante, e então você tem
uma instância.
Ou, opcionalmente, você pode usar o serverless.
Portanto, se for sem servidor,
você não precisará provisionar uma instância.
Então, aqui, quando você vai para as instâncias
provisionadas, não é para fazer serverless, é para fazer o oposto.
Portanto, ao acessar as tarefas, aqui vamos
nós, você pode criar uma tarefa e especificar
o ponto de extremidade do banco de dados de origem que criamos anteriormente,
o ponto de extremidade do banco de dados
de destino que criamos depois e, em seguida, o modo de tarefa.
Portanto, se for provisionada,
precisaremos selecionar a instância provisionada
que criamos anteriormente ou, se for
sem servidor, o DMS ajustará
automaticamente o nível de computação necessário para a tarefa do aplicativo
de erro de migração, e não precisaremos
selecionar o tipo de instância de que precisamos.
Portanto, essa é uma opção mais fácil, eu diria.
Agora você escolhe os tipos de teste.
Então você quer migrar os dados uma vez,
quer migrar e replicar?
Isso significa uma carga
completa e, sempre que os dados de origem forem alterados,
você replicará essas alterações,
o que é chamado de CDC.
Ou você quer apenas fazer a replicação?
E depois, por quanto tempo?
E depois de fazer isso, com base
na sua origem e no seu destino, você pode especificar
algumas configurações e assim por diante para algum
registro, alguma conectividade, como fazer isso, portanto, é um serviço
bastante completo.
Para se aprofundar na configuração de uma replicação, é preciso tempo.
Mas, com essa visão geral,
o que quero mostrar é que você tem uma ideia de
todas as etapas necessárias para configurar o DMS e migrar um banco
de dados de um mecanismo de origem
para um mecanismo de destino, e com duas opções:
instâncias sem servidor
ou provisionadas.
Então é isso, espero
que você tenha gostado
e nos vemos na próxima palestra.
