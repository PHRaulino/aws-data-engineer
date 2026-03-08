Agora vamos
sua infraestrutura de nuvem em uma linguagem de
programação familiar, como JavaScript
ou TypeScript, Python, Java e . NET.
Então, você pode estar
dizendo: "Ei, parece que isso está se sobrepondo ao CloudFormation,
porque no CloudFormation podemos definir a infraestrutura
de nuvem usando YAML.
Mas agora podemos fazer isso usando uma linguagem de programação.
Então, o que é isso? Bem, isso é algo que
substitui o CloudFormation, como veremos
em um segundo momento.
Então, digamos que queremos
definir nossa infraestrutura usando o TypeScript e,
portanto, temos esse código aqui, no qual
estamos definindo três coisas diferentes.
Estamos definindo construções e, portanto,
há componentes de alto
nível que podemos usar graças ao CDK.
Portanto, a primeira construção que estamos usando é uma VPC.
Portanto, criamos uma nova VPC, atribuímos
a ela um nome e três AZs.
E isso cria uma VPC para nós, que
conterá algumas configurações predefinidas.
Em seguida, definimos um cluster ECS.
E o cluster do ECS é chamado de MyCluster e
tem um link para a VPC que acabamos de definir.
Em seguida, definimos um
serviço Fargate com balanceamento de carga
de aplicativo, ou seja, um serviço Fargate com um ALB vinculado
ao cluster que acabamos de definir.
Definimos a quantidade de CPU,
quantas tarefas queremos, portanto,
seis, as opções de imagem da tarefa, os limites de memória
e que queremos um ALB público.
Portanto, tudo isso é definido por meio de uma linguagem
de programação, o que significa que, se não tivermos um código
funcional, se o código não for compilado,
haverá um erro, o que significa
que nosso modelo não poderá ser gerado.
Mas se o código puder ser compilado
porque é sólido e seguro quanto ao tipo, ele
será compilado em um modelo
do CloudFormation.
Pode ser JSON ou YAML.
Portanto, estamos usando o CDK para definir
modelos do CloudFormation no backend.
Mas isso está nos permitindo ser muito mais flexíveis e usar
uma linguagem de programação.
Isso também significa que podemos implementar a infraestrutura
e o código de tempo de execução do aplicativo juntos.
Portanto, isso é ótimo para funções
Lambda, ótimo para contêineres Docker no ECS ou EKS.
Portanto, isso é uma revolução, porque
o modelo do CloudFormation é YAML, não é seguro
para tipos, você pode cometer
erros e só sabe no final se funcionou ou não.
Porém, com o CDK, você pode defini-los usando construções
e uma linguagem de programação.
Portanto, se você quiser um diagrama,
temos nossas construções de aplicativos.
Podem ser funções Lambda, DynamoDB, Amazon S3,
ECS, algumas funções de etapa e assim por diante.
E podemos usar linguagens de programação,
como Python, TypeScript, Java, . NET.
Escrevemos nosso arquivo CDK e, em seguida, sintetizamos
isso usando a CLI do CDK em um modelo do CloudFormation
que aplicaremos ao CloudFormation
para definir nossa infraestrutura.
Portanto, ele está um passo acima do CloudFormation
e facilita muito o trabalho com o CloudFormation.
Então, você pode
me perguntar: qual é a diferença entre CDK e SAM?
Bem, o SAM será focado em sem servidor, e escreveremos
nossos modelos de forma declarativa em JSON ou
YAML, e isso é ótimo para começar
a usar o Lambda rapidamente.
Ele também utiliza o CloudFormation no back-end, certo?
Mas o foco do SAM é a função Lambda e os
aplicativos sem servidor.
Para o CDK, bem, ele é um superconjunto do CloudFormation, portanto, é compatível
com todos os serviços da AWS existentes.
E você escreverá sua infraestrutura com uma linguagem de programação
que você conhece, por exemplo, TypeScript,
Python, Java e . NET e também aproveita
o CloudFormation porque gera
o CloudFormation.
Portanto, esperamos que a diferença entre
esses dois serviços esteja clara.
Há também uma maneira de combinar o CDK
e a estrutura SAM.
Portanto, você pode usar a CLI
do SAM para testar localmente seus aplicativos CDK.
Como?
Bem, primeiro precisamos executar o cdk synth
e, quando fazemos isso,
temos uma função Lambda, digamos, no aplicativo CDK,
executamos o comando cdk synth e isso
vai gerar um modelo do CloudFormation que foi sintetizado
a partir do CDK.
Mas, graças a esse modelo do CloudFormation,
podemos usar a mesma estrutura e fazer a invocação local do SAM, referenciar
o modelo do CloudFormation e chamar a função.
E essas duas estruturas funcionam muito bem juntas.
Portanto, na próxima palestra,
faremos um trabalho prático sobre CDK.
E com essa prática, vamos implantar um aplicativo que nos permite
implantar um bucket S3 no qual os usuários
podem colocar uma imagem.
Esse bucket S3 acionará uma função Lambda que enviará
uma chamada de API ao Rekognition para
analisar a imagem e obter os resultados
de volta do Rekognition e, em seguida, a função
Lambda salvará os resultados no Amazon DynamoDB.
E tudo isso será definido
a partir de um script CDK.
Portanto, vamos fazer isso na próxima palestra.
