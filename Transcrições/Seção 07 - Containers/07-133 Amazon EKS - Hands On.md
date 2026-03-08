um rápido hands-on para o Amazon EKS, mas
isso está completamente fora do nível gratuito.
Portanto, se você decidir fazer isso,
terá um custo bastante alto.
Portanto, sugiro que você
observe o que estou fazendo para entender
um pouco melhor o Kubernetes Service da AWS.
Portanto, vamos criar um novo cluster no AWS.
Por isso, uso DemoEKS como nome.
Posso selecionar uma versão do Kubernetes, mas usarei a padrão.
E então precisamos ter uma função de serviço para
gerenciar tudo.
Portanto, para criar essa função, preciso seguir as instruções
do guia do usuário do EKS.
Então, vou para o IAM e preciso
criar uma função para o EKS e, em seguida,
adicionar a função de cluster do EKS.
Então, vamos fazer isso.
Vamos acessar as funções e criar uma função.
Isso é para um serviço. Isso é para o serviço EKS.
Aqui vamos nós.
E faremos o cluster EKS para permitir
o acesso a outros serviços que são operados
pelo nosso cluster.
Então, aqui vamos nós, estamos bem.
Em seguida, a permissão já está selecionada e o nome da função
é eksClusterRole.
Vamos criar essa função.
Nome inválido, portanto, vamos remover o primeiro espaço
no início.
E agora a função está sendo criada.
Vamos atualizar isso, e podemos
encontrar essa função bem aqui.
Agora, queremos criptografar nossos segredos com o KMS?
Por enquanto, não vou fazer
isso, mas essa é uma possibilidade de segurança.
Então, onde queremos implantar nosso cluster?
Portanto, temos uma VPC e uma sub-rede.
Portanto, estamos altamente disponíveis.
Em seguida, os grupos de segurança que desejamos.
Assim, poderíamos selecionar, por exemplo, o grupo de segurança
padrão e, em seguida, escolher o tipo de serviços IPv4.
Em seguida, o acesso ao endpoint do cluster será público
para que possamos acessá-lo de nosso computador.
Desejamos algum complemento de rede?
Portanto, vamos usar o padrão novamente
e o padrão para proxy e DNS.
Como você pode ver, são muitas configurações
e o EKS deveria ser seu próprio curso, para ser honesto.
Gostaria apenas de mostrar as opções para que você
possa entender o que está acontecendo.
Em seguida, podemos configurar o registro em log para o plano de controle.
Eu não vou fazer isso.
Em seguida, revisamos as configurações.
Portanto, configuramos os grupos de segurança, a rede, o acesso
do endpoint do cluster ao público e estamos prontos para começar.
Então, vamos criar isso.
E o que isso fará é criar o
próprio cluster e, em seguida, teremos
que criar os nós para o cluster.
Portanto, meu cluster foi criado e a próxima etapa é provisionar
a capacidade de computação para seu cluster adicionando
um grupo de nós gerenciados ou criando um perfil
Fargate.
Já vimos isso na visão geral e é exatamente isso
que eu queria mostrar a você.
Portanto, se entrarmos nos recursos, é aqui que todos
os seus recursos do Kubernetes serão gerenciados,
e esse é um conhecimento
específico do Kubernetes, certo?
Mas é aqui que você tem o que precisa para os especialistas em Kubernetes.
Em seguida, na computação, é aqui que podemos adicionar grupos de nós.
Portanto, se eu entrar em grupos de nós, posso adicionar um grupo de nós aqui.
Eu chamo esse grupo de DemoNodeGroup.
Você precisaria criar uma função IAM para esse grupo de nós.
Então, vamos para o console
IAM e criamos uma nova função.
E essa função é para as instâncias do EC2 que fazem parte do meu grupo de
nós gerenciados.
Portanto, usarei apenas
o EC2 e depois procurarei por políticas.
Digitarei EKS, e você
deseja adicionar uma AmazonEKSWorkerNodePolicy.
Então, vamos clicar em "next" (próximo) e, para isso, vou digitar e está
em algum lugar na documentação.
Então, vou inserir o AmazonEKSNodeRole e, na
verdade, há permissões adicionais para isso.
Em seguida, precisamos
adicionar também o AmazonEC2ContainerRegistryReadOnlyPolicy.
Então, vamos voltar.
Aqui, vamos editar as permissões
e adicionar mais uma coisa, o AmazonEC2ContainerRegistry.
Então, vamos procurar por isso. Aqui vamos nós.
Ele está aqui, é o próximo e estamos prontos para começar.
Vamos criar essa função.
Portanto, vamos nos certificar de que ele não comece com um espaço.
Aqui vamos nós.
A função foi criada
e agora posso entrar aqui, atualizá-la, e encontrarei
o AmazonEKSNodeRole.
Excelente.
Então, queremos ter um modelo de lançamento
para nossas instâncias do EC2?
Podemos especificar um, mas deixarei essa opção desmarcada
e clicarei em Avançar.
Que tipo de grupo de nós queremos?
Portanto, o Amazon Linux 2 é excelente.
Queremos instâncias sob demanda ou pontuais?
Que tipo de instâncias queremos?
Também queremos o t3. médio, t3. micro, o que você quiser.
Qual é o tamanho do disco?
Qual é a configuração de dimensionamento de nós?
Então, quantos nós em seus grupos de nós você deseja?
Portanto, essas são as configurações do grupo de dimensionamento automático.
E o que são as atualizações do grupo de nós?
Então, quando você faz atualizações,
quantos nós você pode tolerar que sejam feitos?
Então, clique em next, a quais sub-redes você deseja ter acesso?
E, quando estivermos prontos, criaremos
esse grupo de nós gerenciados.
Portanto, para mostrar isso, esta
é a maneira de implantar instâncias do EC2 para o cluster do
Amazon EKS, mas elas são totalmente gerenciadas
pelo AWS, o que facilita muito.
E a outra maneira de criar nós aqui é subir
um nível e voltar para a computação.
A outra maneira de criar nós, exceto a partir desse grupo
de nós, é ter o Fargate.
E o Fargate permite que você não provisione instâncias do EC2.
Assim, teríamos uma configuração para adicionar
um perfil de destino.
Não vamos fazer isso, apenas quero
mostrar as opções de grupos de nós para perfis
do Fargate.
Na verdade, não preciso deste, portanto,
vou excluí-lo quando terminar de criar.
E a última opção que quero mostrar a você é sobre complementos.
Portanto, se quisermos realmente usar volumes EBS, podemos
instalar complementos,
e um deles é o driver Amazon EBS CSI.
Isso nos permitirá aproveitar o EBS para
o nosso cluster Amazon EKS, e eles
também serão um driver lateral CSI
para FSX, EFS e assim por diante.
Ok, então essas são todas as ações que quero mostrar a você.
Para ser honesto, o Kubernetes requer seu próprio conhecimento,
é muito, muito difícil e exige
um curso completo sobre ele.
Portanto, o que vou fazer agora
é excluir esse cluster.
Portanto, para isso, digitarei DemoEKS e pronto.
Tudo o que eu queria mostrar a você era como criar um cluster EKS.
E para excluí-lo, primeiro preciso excluir os grupos de nós.
Vou pular essa parte do vídeo.
Então é isso para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
