Portanto, o SAM é esse pequeno
esquilo, mas também é o modelo de aplicativo sem servidor.
Trata-se de uma estrutura real para desenvolver
e implementar aplicativos sem servidor.
Isso significa que você escreverá
seu código e usará uma configuração no formato
YAML, que estará em conformidade com a estrutura
SAM.
E, automaticamente, o SAM vai gerar arquivos
CloudFormation muito complexos
a partir de arquivos SAM YAML simples.
Ele é compatível com qualquer coisa do CloudFormation.
Portanto, você ainda pode usar saídas, mapeamentos,
parâmetros, recursos, etc. em seu código SAM YAML.
Agora, o SAM em segundo plano também pode usar o CodeDeploy para
implantar funções do Lambda, e
o SAM pode ajudá-lo a executar o Lambda, o API Gateway
e o DynamoDB localmente.
Portanto, o SAM realmente
pretende se concentrar em aplicativos sem servidor e permitir
que você os depure localmente e os implemente
rapidamente usando o CloudFormation
na nuvem da AWS.
Portanto, o SAM é feito de receitas
e, na parte superior do seu modelo, você adicionará um cabeçalho
de transformação para indicar que
se trata de um modelo SAM.
E este é um cabeçalho de transformação
que dirá ao CloudFormation para transformá-lo
em um modelo do CloudFormation.
Em seguida, você escreve
seu código, mas, em vez de usar as construções
do CloudFormation, usará as construções
do SAM, como uma função sem servidor, que é uma função Lambda,
uma API sem servidor, que será o gateway de API, e o SimpleTable
sem servidor, que será o DynamoDB.
Mas você tem essas construções para simplificar
e facilitar a criação de seus aplicativos sem servidor.
E, para empacotar e implantar esse aplicativo no AWS, você
usará o comando sam deploy.
E costumava ser dois comandos.
Costumava ser o sam package e depois o sam deploy.
Mas agora você pode simplesmente fazer a implantação do Sam
por conta própria, e ele também o empacotará para você.
Há também uma maneira de sincronizar suas alterações
no AWS Lambda muito rapidamente usando o SAM Accelerate,
e o comando é sam sync e depois minus minus watch.
Darei a você um pouco
mais de informações sobre isso nesta palestra.
Então, vamos dar uma olhada na implantação do SAM.
Portanto, você tem o código do aplicativo
e o modelo SAM no formato YAML e, em seguida, criará o
aplicativo localmente usando
o sam build.
Ele se transformará em um modelo do CloudFormation e no código do
seu aplicativo e, em seguida,
você poderá implantá-lo usando o sam deploy.
Portanto, você compactará e carregará tudo em um bucket S3 e, em
seguida, executará automaticamente
o ChangeSet no CloudFormation.
Em seguida, sua pilha do CloudFormation
pode ser composta de diferentes componentes sem
servidor, como Lambda, API Gateway e DynamoDB.
Então, vamos falar sobre o SAM Accelerate.
Portanto, o SAM Accelerate é o conjunto de recursos usado para reduzir
a latência durante a implementação de recursos no AWS.
Portanto, você deseja implementar o mais rápido possível.
E o comando será sam sync para
declarar seu projeto,
declará-lo com um modelo SAM no AWS.
E, na verdade, ele contornará o CloudFormation se
você fizer apenas alterações
no código sem atualizar sua infraestrutura usando
a API de serviço.
Portanto, será uma implantação muito, muito rápida.
Portanto, você tem o modelo SAM, o código do
aplicativo e a função Lambda já implantados e vai executar
a sincronização de amostra.
E automaticamente, à medida que você altera o código do aplicativo,
o SAM sincronizará automaticamente o código dele com
a função Lambda.
Portanto, se você quiser testar sua função
Lambda na nuvem, isso será muito fácil e muito rápido.
Portanto, há diferentes opções: você
pode simplesmente executar o sam sync para sincronizar o código e a infraestrutura,
ou o sam sync e apenas a opção de código
para sincronizar somente o código e não a infraestrutura.
Portanto, você não usará o CloudFormation,
pois as atualizações serão feitas em segundos.
Em seguida, você pode especificar um recurso específico
para dizer: "Quero atualizar apenas minhas funções
Lambda e suas dependências,
ou quero atualizar essa função Lambda específica usando
o ID do recurso".
Ou você pode usar a opção de observação, que
monitorará as alterações nos arquivos.
Portanto, ele será executado em
segundo plano e sincronizará automaticamente qualquer coisa
quando forem detectadas alterações.
Portanto, se você incluir a configuração, usar o sam
sync ou se for apenas um código,
ele usará o sam sync e, em seguida,
a opção de código.
Espero que isso faça sentido.
Espero que essa seja uma boa visão geral do SAM.
Também faremos algumas práticas
para que fique claro para você como isso funciona.
Portanto, espero que tenham
gostado desta palestra e nos vemos na próxima.
