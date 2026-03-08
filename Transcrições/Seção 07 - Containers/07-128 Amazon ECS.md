ECS, e teremos uma visão
geral de todos os seus aspectos.
Portanto, a primeira coisa sobre a qual
quero falar com você é o tipo de lançamento do EC2.
Portanto, ECS significa Elastic Container Service.
E quando você inicia contêineres do Docker
no AWS, está lançando o que é chamado de tarefa do ECS no cluster do ECS.
E um cluster ECS é feito de coisas.
E com o tipo de lançamento do EC2,
bem, essas coisas são instâncias do EC2.
E, nesse caso, se você
usar um cluster do ECS com um tipo de lançamento do EC2,
deverá provisionar e manter a infraestrutura por conta própria.
Isso significa que seu Amazon ECS/ ECS Cluster
será composto de várias instâncias do EC2.
Agora, essas instâncias
são um pouco especiais porque cada uma delas deve executar
o ECS Agent e, em seguida, esse agente registrará
cada instância do EC2 no serviço Amazon ECS e no
cluster ECS especificado.
Agora, quando você tiver isso
em vigor, ao iniciar as tarefas do ECS, o
AWS iniciará ou interromperá os contêineres.
Isso significa que, sempre que tivermos um novo
contêiner do Docker, ele será colocado adequadamente
em cada instância do EC2 ao longo do tempo, como você pode ver aqui.
E você pode iniciar ou parar a tarefa do ECS, e ela será
colocada automaticamente.
Esse é o tipo de lançamento
do EC2, e os contêineres do Docker são colocados em instâncias
do Amazon EC2 que provisionamos com antecedência, certo?
Agora, há um segundo tipo de lançamento
chamado Fargate Launch Type.
E, novamente, você inicia contêineres do Docker
no AWS, mas dessa vez não provisiona a infraestrutura, portanto
não há instâncias do EC2 para gerenciá-la.
É tudo sem servidor.
Bem, porque não gerenciamos servidores,
mas é claro que há servidores por trás.
Portanto, no tipo Fargate, se tivermos um
cluster ECS, basta criar uma
definição de tarefa para definir nossas tarefas ECS.
Em seguida, o AWS executará essas tarefas de ECS para nós com base na
quantidade de CPU e RAM de que precisamos.
Portanto, quando quisermos executar um novo contêiner
do Docker, ele será executado, sem que saibamos
onde ele será executado e sem que uma instância
do EC2 seja criada no back-end em nossas contas para
que ele funcione.
Portanto, é um pouco mágico.
E para escalar, bem, você só precisa aumentar o número
de tarefas.
Simples, você não precisa gerenciar
mais instâncias do EC2.
E o exame adora dizer para você usar o Fargate
porque o Fargate é sem servidor e é muito mais
fácil de gerenciar do que o EC2 Launch Type.
Bem, já vimos os dois tipos de lançamento do Amazon ECS.
Agora vamos falar sobre as funções de IAM para as tarefas do ECS.
Então, vamos dar um exemplo do tipo de lançamento
do EC2 no qual temos uma instância
do EC2 executando o ECS Agent no Docker.
Portanto, nesse caso, podemos criar um perfil de instância do EC2
que só é valorizado, é claro,
se você usar o EC2 Launch Type.
Ele será usado apenas pelos agentes do ECS e, em seguida, o agente do
ECS usará o perfil de instância do EC2 para fazer chamadas de API ao serviço
do ECS para restaurar a instância e fará
chamadas de API ao CloudWatch
Logs para enviar registros de contêineres.
Ele usará as chamadas de API para o ECR,
para extrair imagens do Docker do ECR
e também fará referência a dados
confidenciais no Secrets Manager ou no SSM Parameter Store.
E nossas tarefas do ECS receberão funções de tarefas do ECS.
Portanto, isso é avaliado tanto
para o EC2 Launch Type quanto para o Fargate.
Portanto, tenho duas tarefas.
E podemos criar uma função específica por tarefa.
Portanto, minha primeira tarefa A terá uma função de tarefa
A do ECS, e a primeira tarefa B e a segunda
tarefa B terão a função de tarefa B.
Bem, por que temos funções diferentes?
Porque cada função permite que você seja vinculado
a diferentes serviços do ECS.
Assim, por exemplo, a função ECS Task A permite que
você tenha sua Task A, que executa algumas
chamadas de API no Amazon S3.
Já a função Task B permite que você execute, novamente,
chamadas de API no DynamoDB.
E você define a função
da tarefa na definição da tarefa do seu serviço ECS.
Portanto, lembre-se disso, a distinção
entre a função de perfil de instância do EC2 e a função de tarefa do ECS.
Em seguida, Integrações do balanceador de carga.
Portanto, no exemplo, estou no tipo de lançamento EC2,
mas também poderia ser Fargate, é claro,
e tenho várias tarefas ECS em execução.
Tudo isso está no cluster ECS.
E queremos expor essas tarefas
como um ponto de extremidade HTP ou HTTPS.
Portanto, podemos executar um Application
Load Balancer na frente dele e, assim, nossos usuários
irão para o ALB e, no back-end, para as tarefas do ECS diretamente.
Portanto, nesse caso,
o ALB é suportado e suportará a maioria dos casos de uso, e essa é
uma boa escolha.
O balanceador de carga de rede é recomendado somente
se você tiver casos de uso de taxa de transferência
muito alta ou de alto desempenho ou, como
você aprenderá mais adiante neste curso,
se usá-lo com o AWS Private Link.
Ou, se você quiser usar a geração
mais antiga do Classic Load Balancer, poderá fazê-lo,
mas definitivamente não é recomendado porque
você não obtém nenhum recurso avançado
e não pode vincular o Elastic Load Balancer ao Fargate.
Por outro lado, se você estiver usando o Application Load
Balancer, ele funcionará, é claro, com o Fargate.
E quanto aos dados persistentes no Amazon ECS?
Para isso, você precisa
de um volume de dados, e há vários
tipos, mas um deles é notável: o EFS.
Digamos que você tenha um
cluster ECS e, nesse caso, esteja representando a instância
EC2 e o tipo de lançamento do Fargate para o meu cluster ECS.
E queremos montar um sistema de arquivos
na tarefa ECS para compartilhar alguns dados.
Nesse caso, usamos um sistema de arquivos Amazon EFS, pois é um sistema
de arquivos de rede que será compatível com os
tipos de lançamento do EC2 e do Fargate.
E isso nos permite montar o sistema de arquivos
diretamente em nossas tarefas ECS.
Por quê? Bem, então as tarefas executadas
em qualquer AZ vinculada a esse sistema de arquivos Amazon EFS compartilharão
os mesmos dados e, portanto, poderão
se comunicar com outra por meio do sistema de
arquivos, se desejarem.
Portanto, a combinação definitiva
é usar o Fargate para iniciar a tarefa do ECS de forma
sem servidor e o Amazon EFS para
o sistema de arquivos persistente, porque o EFS também
é sem servidor, não gerenciamos nenhum
servidor, é pago conforme o uso.
Ele é provisionado com antecedência e você está pronto para começar.
Portanto, os casos de uso do EFS com o ECS são para fazer
armazenamento compartilhado multi-AZ persistente
para seus contêineres.
