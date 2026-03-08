ECS, e vamos criar nosso primeiro
cluster.
Portanto, no lado esquerdo, vamos clicar
em
Clusters e, em seguida, em Create cluster.
Portanto, o nome do cluster pode ser o que
você quiser.
Por exemplo, DemoCluster.
E, em Infraestrutura, temos a maneira
de selecionar como obter capacidade.
Portanto, agora temos várias opções.
E as opções são apenas Fargate.
Isso é sem servidor. Você não pensa em
servidores, e o AWS os fornecerá para
você.
Você tem instâncias Fargate e Manage
Instances, e instâncias Fargate e
Self-managed.
Portanto, essa é a maneira antiga de
gerenciar suas
instâncias do EC2, e você precisa criar um
grupo
de dimensionamento automático e, em
seguida, selecionar o tipo
de AMI que deseja, o tipo de instância
do EC2 que deseja e assim por diante.
É bom ver essas opções, mas
não vamos falar sobre isso
porque agora a AWS está
tentando afastá-lo das instâncias
autogerenciadas.
O Fargate e o Managed Instances
são muito semelhantes, pois também teremos
o Fargate, mas o AWS também
gerenciará nossas instâncias EC2 nos
bastidores.
E aqui o que temos que fazer
é criar um perfil de instância.
Portanto, você pode clicar em Criar novo
perfil de instância bem aqui.
E isso é para o ECS.
E isso é para a função EC2 para instâncias
gerenciadas pelo ECS.
E clicamos em Next.
E isso é chamado de ecsInstanceRole.
E clique em Create role (Criar função).
Portanto, minha função já existe, então
vou usar essa função aqui
e estou pronto para começar.
E, em seguida, para a função de
infraestrutura,
vou criar uma nova função de
infraestrutura.
Eu desço a tela.
Você usa este aqui, Infrastructure for ECS
Managed Instances (Infraestrutura para
instâncias gerenciadas do ECS).
Próximo. Esta é uma nova
função, portanto, vou criá-la.
E agora minha função foi criada.
Então, voltando ao assunto, posso
colocá-lo bem aqui.
E estamos prontos para começar.
Em seguida, temos a seleção instantânea.
Então, queremos que o ECS escolha por
padrão com base na definição do
teste e nos requisitos do serviço?
E para uma carga de trabalho
de produção, isso é definitivamente
necessário.
Ou você quer usar o personalizado? Nesse
caso, você
escolheria entre o atributo vCPU e a
memória,
dizendo a quantidade mínima e máxima que
deseja.
Portanto, isso é mais avançado.
Além disso, se você quisesse forçar,
por exemplo, um tipo de instância
específico, diria Allowed instance type.
E você diria, por exemplo, apenas
t3.micro.
É isso aí.
E então você só teria o
t3.micro como parte dessas instâncias
gerenciadas.
Portanto, é muito bom porque o AWS
vai gerenciar essas instâncias para você.
Em seguida, você pode clicar em Criar.
Agora, para ser compatível com as
próximas palestras que fiz, mas são
coisas muito semelhantes, em vez de
gerenciar nossas instâncias, teremos
instâncias autogerenciadas.
Aqui, vamos criar um novo grupo
de dimensionamento automático sob demanda.
Especificamos o tipo de instância como
sendo t3.micro.
Em seguida, usaremos a função padrão para
a função de instância do EC2.
Dizemos que no máximo 2. Não há
necessidade de SSH.
Especificamos o tamanho mínimo do volume
do EBS raiz de 30 gigabytes.
Em seguida, deixamos tudo para as
configurações de
rede como padrão e clicamos em Create.
Então, enquanto isso acontece, vamos dar
uma
olhada no grupo de dimensionamento
automático
que está sendo criado no AWS.
E, no lado esquerdo, clicarei
em Auto Scaling Groups aqui.
E está mostrando, como você pode ver,
que foi criado um grupo de
dimensionamento automático para mim
chamado Infra-ECS-Cluster.
E essas são a capacidade 0, a capacidade
mínima 0 e a capacidade máxima 5.
E isso foi criado diretamente pelo meu
cluster ECS.
E a criação está em andamento.
E o que esse cluster
tem, talvez tenhamos instâncias EC2
para que eu inicie tarefas.
Portanto, podemos ver que ele está em três
zonas disponíveis e duas zonas.
Portanto, sabemos que as tarefas do
ECS serão lançadas em três AZ.
E o que vou fazer agora é
esperar que esse cluster seja criado,
o que é o caso agora.
Portanto, o que posso fazer agora é
explorar esse DemoCluster.
Portanto, se eu clicar nele, estarei no
DemoCluster
e poderei acessar Services, are 0, tasks
are 0 porque ainda não lançamos nada.
E depois vamos para o mais interessante, a
infraestrutura.
Portanto, se você for até a
Infraestrutura, temos
três provedores de capacidade nesse
cluster do ECS.
O primeiro é o FARGATE.
Isso significa que podemos iniciar a
tarefa Fargate em nosso cluster ECS.
O segundo é FARGATE_SPOT.
Isso significa que podemos iniciar a
tarefa Fargate no
modo Spot e selecionar instâncias Spot
para o EC2.
E o último é um provedor de ASG.
E isso significa que podemos iniciar
instâncias do
EC2 nesse cluster diretamente por meio
desse ASG.
Portanto, o dimensionamento é gerenciado
no momento,
e o tamanho atual é 0.
Mas posso mudar isso se quiser.
Então, deixe-me mostrar a você como seria.
Eu vou aqui, vou para Detalhes e
edito a capacidade desejada para 1, só
para mostrar a você como é.
Portanto, o que acontecerá com isso
é que uma instância do EC2
será criada, certo? E quando for
criada, ela se registrará no DemoCluster.
Em seguida, eu o verei em Instâncias de
contêineres.
Isso significa que, quando criamos uma
tarefa do
ECS, ela pode ser iniciada em um provedor
de capacidade Fargate ou Fargate Spot, ou
pode ser iniciada nas instâncias de
contêineres
que eu lançarei como parte desse ASG.
Portanto, o que vou fazer agora
é esperar que essa instância esteja
em estado de execução e registrada
no meu cluster do ECS.
Então, deixe-me atualizá-lo.
Minha instância está em serviço e é
t2.micro.
E se eu voltar ao meu cluster do
Amazon ECS, ele será registrado como uma
instância de contêiner que, no momento,
obviamente,
está executando 0 tarefas e tem 1024
CPU disponíveis e 982 de memória
disponível.
Portanto, isso está me fornecendo a
capacidade dessa
instância, e posso iniciar, como você
verá, tarefas
nela até que a capacidade se esgote.
Então, estamos prontos para ir.
Portanto, temos um cluster ECS.
Vimos dois provedores de capacidade. Três.
Já vimos as instâncias de contêineres.
Então, agora vamos executar nosso primeiro
serviço.
E eu o verei na próxima palestra para
fazer isso.
