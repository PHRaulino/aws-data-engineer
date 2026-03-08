Mas, antes disso, precisamos criar uma definição de tarefa.
Portanto, vou criar uma nova definição de tarefa nos
painéis de definição de tarefa e preciso dar um nome a ela.
Portanto, vou chamá-lo de nginxdemos-hello.
E isso vem dessa imagem do
docker chamada nginxdemohello no docker hub.
Portanto, este é o que usaremos em nossa demonstração.
Por isso, chamo minha definição de teste de
nginxdemo com um hino de hello.
Em seguida, precisamos escolher
os requisitos de infraestrutura.
Então, queremos lançar em instâncias
do Fargate ou do Amazon EC2.
Bem, o Fargate é computação sem servidor, portanto,
vamos deixá-lo ativado.
E se habilitarmos isso, poderemos iniciar essa tarefa,
esse serviço em nossas instâncias do Amazon EC2.
Mas, para simplificar, agora
vou usar apenas o AWS Fargate e
lançar nossos contêineres em dois modos de computação sem servidor.
Em seguida, precisamos escolher o tipo de
sistema operacional e a arquitetura que temos.
Portanto, o Linux é bom.
E qual é o tamanho da tarefa para o nosso contêiner Fargate?
Portanto, podemos dizer, por exemplo, que temos 0. 5 ou uma vCPU, e você pode
ir até 16 vCPU neste exemplo.
E você também pode ajustar a memória.
Assim, você pode dizer, ei, eu quero, por exemplo, até
120 gigabytes de memória.
Portanto, tudo isso seria
fornecido pela Fargate em um modo sem servidor.
Para manter as coisas bem baratas
e simples, escolherei 0. 5 vCPU e um gigabyte.
Em seguida, temos a função da tarefa.
Portanto, a rolagem de tarefas é uma função de IM que podemos
atribuir à nossa tarefa se quisermos fazer uma solicitação
de API aos serviços do AWS.
Mas como não estamos fazendo isso no momento, não vamos especificar
uma função de tarefa.
Mas isso é de extrema importância
se os seus contêineres precisarem usar o AWS.
Agora, para a função de execução de tarefa, deixe-a
como padrão e, se essa função de execução de tarefa do ECS ainda não tiver sido
criada, ela será criada automaticamente pelo serviço do ECS.
Portanto, estamos bem.
Em seguida, nosso contêiner.
Portanto, o nome será nginxdemos-hello.
E o URL da imagem será nginxdemoshello/hello.
E isso vai puxar automaticamente essa imagem
do hub do docker bem aqui.
Portanto, ele é muito prático e é um recipiente essencial.
Agora temos muitas opções diferentes.
Por exemplo, os mapeamentos de porta.
Portanto, queremos mapear a porta 80 para a porta
80 do contêiner, o que é ótimo, e vamos deixá-la como está.
E então você poderia adicionar mais mapeamentos de portas, se quisesse.
Você pode, por exemplo, definir os limites de alocação de recursos,
as variáveis de ambiente a partir de um arquivo
ou manualmente e o registro em log.
Mas vou deixar todas essas coisas como padrão,
pois isso funcionará bem para nós.
Armazenamento, o Fargate vem com algum armazenamento efêmero.
Portanto, vamos deixar como está novamente, de 21 gigabytes,
que é o padrão aqui.
E isso é bom, basta deixar o valor que você tem no momento.
Então, vamos criar isso.
E isso está criando nossa primeira definição de tarefa.
Agora você vê a versão dois para mim porque
acabei de criá-la duas vezes.
Mas, para você, é melhor ver a versão um.
Em seguida, vamos lançar essa definição de tarefa como uma pesquisa.
Então, vamos entrar nos clusters e depois no cluster de demonstração.
E, em serviços, vou criar um serviço.
Certo, então devo especificar os detalhes do serviço.
Portanto, primeiro vamos selecionar uma família de definição de tarefa.
Escolheremos o nginxdemoshello.
Em seguida, você escolhe a revisão de definição de tarefa
que estiver disponível para você.
Escolhi o mais recente, que é o número dois para mim.
E, em seguida, nome do serviço, você pode manter
isso ou remover isso, o que quiser.
Agora, o nome do serviço será
criado nesse cluster.
Precisamos escolher a configuração de computação.
Portanto, usaremos a estratégia do provedor
de capacidade, a deixaremos como padrão e usaremos
o Fargate para iniciar nossos próprios serviços e tarefas.
Ok, a versão da plataforma também será a mais recente.
Não tocamos em nenhum deles.
Para a configuração da implantação, que é uma réplica.
Portanto, teremos várias tarefas em nosso cluster.
E, neste momento, queremos uma tarefa.
Mas se você quiser mais tarefas, por
exemplo, selecione quatro e terá quatro contêineres do nginxdemo
disponíveis para você.
Mas queremos mantê-lo pequeno para reduzir o custo ao mínimo.
Então, deixamos tudo como está para o rebalanceamento do AZ.
Esse é um recurso do ECS para reequilibrar,
caso você tenha muitas tarefas em uma
AZ específica.
Não tocamos em nenhuma das opções de implantação nem nisso.
Para a rede, vamos entrar aqui, estamos bem
com essas sub-redes, vamos
criar um novo grupo de segurança.
Posso manter esse nome, está tudo bem.
E então permitiremos o tráfego HTP de qualquer lugar.
Isso nos permite acessar a porta 80 do nosso serviço nginx.
Ok, em seguida, usaremos o IP público para ativar, sim, perfeito.
E, para o balanceamento de carga, vamos
permitir o balanceamento de carga.
Para ter um balanceador
de carga, temos um balanceador de carga de aplicativos.
Ele será conectado à porta 80 da nossa demonstração do nginx.
Vamos criá-lo, vou chamá-lo de DemoALBForECS.
Listener na porta 80, E então
vamos criar um novo grupo de destino,
nginxdemosTG.
Na porta 80, estamos prontos para começar.
E então não tocaremos na rede VPC.
Não tocaremos no dimensionamento automático do serviço,
pois queremos aumentar e diminuir
o dimensionamento com base no alarme do CloudWatch.
Não configuraremos nenhum volume.
Vamos criar esse serviço.
Portanto, nosso serviço foi implantado com sucesso.
Então, vamos clicar no serviço e dar uma olhada nele.
Portanto, como podemos ver agora, temos uma tarefa
desejada, uma que está em execução e o status é ativo.
Portanto, isso é muito bom.
E podemos ver que o serviço
está vinculado a um grupo-alvo.
Então, clico no grupo de destino e, no próprio
grupo de destino, podemos ver que ele está vinculado
ao nosso demoALB, que é o balanceador de aplicativos
que foi criado como parte desse serviço.
E parece que um endereço IP está registrado como alvo.
E este é o endereço IP
do meu contêiner, o que é muito bom.
Agora, se dermos uma olhada no balanceador de carga
em si, ele está ativo, posso copiar o nome do DNS,
abrir uma nova guia e colá-lo.
E recebo a página de boas-vindas do nginx, que é muito boa.
Isso significa que tudo está funcionando.
O endereço do servidor é exatamente
o mesmo que o IP que registramos aqui.
Portanto, esse é o IP privado, o que é bom.
E o que mais?
Portanto, se entrarmos no próprio serviço,
poderemos dar uma olhada nas tarefas.
Portanto, como você pode ver, um contêiner está em execução
no momento, e essa é a única tarefa.
Posso clicar nela e dar uma olhada na tarefa em si.
Assim, ele me informa a configuração, a revisão da tarefa, onde
ela foi iniciada, o IP privado, os contêineres.
Podemos dar uma olhada nos logs para
conhecer os logs do nosso contêiner nginx também, o que é bom.
E se analisarmos o serviço em si, ou seja, se estivermos
no serviço e depois formos
para os eventos, poderemos ver quais foram os eventos
desse serviço.
Isso significa que temos uma tarefa que foi iniciada.
Ele foi registrado no grupo Atari e, em seguida,
foi totalmente implementado, e agora temos
um estado estável.
Portanto, como podemos ver aqui, posso ir para o teste de
barra, por exemplo, e o URI será alterado aqui.
Portanto, o nginx está funcionando como esperado.
Agora, o que podemos fazer, porque estamos no ECS, é dar
uma olhada em nossa tarefa.
Temos um deles, mas podemos lançar mais alguns.
Portanto, mostrarei a você como é fácil lançar mais
tarefas com a Farget.
Portanto, vamos atualizar esse serviço.
E agora o número desejado de tarefas será três.
Portanto, um por AZ, por exemplo, e o restante
eu deixarei como está.
Portanto, deixaremos a definição do teste como está.
Deixaremos a configuração de computação como Fargate e o balanceamento de carga não muda
em termos de verificações de integridade e
assim por diante.
Então, vamos clicar em atualizações.
E agora o que vai acontecer é que pedimos ao serviço
ECS para executar mais duas tarefas.
Portanto, se eu atualizar
isso e esperar um pouco, agora temos mais
duas tarefas sendo provisionadas e elas são provisionadas
no mecanismo Fargate.
Isso significa que, nos bastidores, o AWS
provisionará automaticamente o recurso necessário para
iniciar essas tarefas.
Portanto, vamos esperar um pouco. Eles estão pendentes.
Agora eles estão sendo ativados e estão funcionando.
Na verdade, isso foi muito rápido.
E se eu for até aqui e atualizar
a página, como você pode ver, o endereço
IP está mudando toda vez que eu atualizo.
Portanto, o balanceador de aplicativos está distribuindo
a carga entre todos os meus contêineres no ECS, o que é ótimo.
Portanto, isso é muito poderoso
e acabamos de demonstrar o dimensionamento
do ECS durante o aumento de escala.
E apenas para reduzir a demonstração
e economizar custos, podemos atualizar o serviço aqui e fazer
com que o número desejado de tarefas seja zero.
Dessa forma, o serviço ainda está lá, mas
não temos nenhum contêiner em execução.
E, em meu aplicativo, meu grupo de dimensionamento automático, desculpe,
então vou clicar nele e me certificar
de que a capacidade desejada também seja zero.
Dessa forma, temos certeza de que não estaremos executando
nenhum tipo de instância em nosso cluster EC2 para o ECS.
Está bem?
Portanto, agora você pode verificar isso,
que as tarefas foram eliminadas e que você está pronto para prosseguir.
E você pode examinar os eventos para
ver o que o ECS fez enquanto pedíamos que ele
atualizasse o serviço.
Está bem? Então é isso.
Vimos como criar um cluster ECS, vimos como
criar um serviço ECS no Fargate.
Espero que tenham gostado e nos veremos na próxima palestra.
