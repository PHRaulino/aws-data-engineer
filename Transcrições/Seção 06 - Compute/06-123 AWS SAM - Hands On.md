usar a estrutura SAM e, para isso,
queremos iniciar um Cloud Shell clicando aqui.
Ele iniciará o ambiente e preparará seu terminal e,
em seguida, praticarei o uso da CLI do SAM.
Portanto, como você pode ver, se eu fizer a versão SAM menos menos, a CLI do SAM
deverá ser instalada por padrão no Cloud Shell, o que torna
muito fácil começarmos.
E então fazemos a SAM init.
Assim, com o Sam init, podemos inicializar nosso aplicativo
diretamente usando a CLI do Sam.
Portanto, podemos usar um modelo Quick Start ou um local
de modelo personalizado.
Mas como estamos tentando fazer demonstrações,
vamos criar um modelo de Início Rápido digitando um.
E então temos várias opções.
Portanto, temos 16 opções para escolher, como
Hello World Example, processamento de dados, API
sem servidor, exemplo do DynamoDB e assim por diante.
Portanto, há muitos exemplos.
Neste momento, começaremos de forma
simples e faremos um exemplo do Hello World.
Então, um, e depois queremos usar o Python 313 e o zip? Sim.
Deseja ativar o rastreamento de raios X? Não, por enquanto.
Deseja ter insights sobre o CloudWatch? Não.
Deseja o formato de registro JSON? Não.
E o nome do produto será apenas SAM app, enter
e pronto.
Portanto, agora esse aplicativo SAM foi gerado, e podemos
verificar isso executando o aplicativo CD SAM para entrar
no diretório do aplicativo SAM.
E então eu posso encontrar. menos a impressão.
Ele imprimirá todos os arquivos que estão em meu diretório.
Portanto, temos o diretório Hello World,
temos o diretório de teste, temos o diretório de eventos e, em seguida,
temos vários arquivos.
Portanto, os arquivos que são muito importantes de serem examinados,
por exemplo, são o aplicativo Hello World. py.
Portanto, este arquivo, bem aqui, vou copiá-lo,
fazer cat e, em seguida, o arquivo nos mostrará
o conteúdo do arquivo.
Portanto, esse arquivo contém nosso
aplicativo que será
em Python e que será enviado para o Lambda
quando o aplicativo SAM for implantado.
Portanto, importamos o JSOM, temos uma função de manipulador
Lambda, que receberá um evento
e retornará um "Hello world" como resposta.
Muito fácil, muito simples. Vamos voltar aos nossos arquivos.
Outro arquivo importante é o arquivo de requisitos.
Este define os pacotes Python que são importantes.
Aqui temos o pacote Python de solicitação que é importante.
Depois, temos outros arquivos que são importantes,
como a configuração do SAM. 2 ml.
Portanto, este aqui, ops, com um ponto aqui.
Portanto, este é o arquivo de configuração do nosso
aplicativo SAM, no qual são definidos a versão, o nome da
pilha, os parâmetros de compilação e assim por diante.
Configurações tão importantes se você quiser
usar o Sam, é claro, em um nível mais alto.
E, por fim, temos o modelo. yamo.
Portanto, esse arquivo também
é importante porque é um modelo de aplicativo sem servidor.
Portanto, podemos ver aqui que temos
a transformação AWS serverless que nos diz que se trata de modelos especiais
de transformação de nuvem.
Ele é destinado ao SAM e, nele, definimos
tudo o que precisamos para o SAM.
Portanto, temos, por exemplo,
a função timeout e temos recursos.
Aqui, o tipo é uma função sem servidor, e aqui
temos o URL do código, o manipulador, o tempo de execução.
Assim, tudo fica um pouco
mais fácil e segue a documentação da estrutura SAM.
Agora, vamos implementar essa função.
Portanto, vou usar o SAM Build para criar nosso aplicativo.
Portanto, aqui recebemos um erro
do Python porque o Python 3 dessa versão específica não
está instalado.
Portanto, aqui temos o Python 3. 9. 23.
Portanto, usaremos o Python 3. 9, portanto, em
nossa função, que é uma versão
de suporte do Lambda no momento, o que é útil,
e esperamos que eles atualizem
a versão do Python com o tempo.
Portanto, use a versão que encontrar em sua CLI do SAM.
Certo, então vamos aos nossos arquivos e queremos
atualizar o modelo. yamo.
Portanto, farei um modelo nano. yamo para atualizá-lo.
E lá, eu desço a tela.
E aqui, para o tempo de execução, usarei apenas o Python 3. 9.
E esse deve ser o truque.
Portanto, pressione Ctrl X e, em seguida, Y e Enter para salvar o arquivo.
Controle X, Y enter.
Podemos verificar isso cortando o arquivo e, como você
pode ver, agora ele diz Python 3. 9.
Assim, podemos tentar novamente o mesmo comando de compilação.
Então, fazemos a mesma construção.
Agora a compilação foi bem-sucedida e temos artefatos de compilação.
Portanto, agora há um diretório chamado AWS SAM app ls.
Vamos fazer isso novamente, rs.
E aqui temos...
E, é claro, meu erro, é com um ponto.
Portanto, LS. AWS, SAM app, e aqui temos um
diretório que foi criado
pela estrutura SAM, no qual temos a compilação
e o cache, as dependências e os dois arquivos
ML, que informam como ele foi compilado.
Portanto, nesse diretório chamado build, você pode dar uma olhada.
Encontraremos a função Hello World
e nosso modelo. arquivo yamo.
E na função Hello World, encontraremos todos os nossos pacotes, bem como
o código do aplicativo, que é app. py.
Portanto, aqui fizemos algumas coisas.
Criamos nosso aplicativo SAM e, portanto, agora podemos
fazer muitas coisas.
Podemos validar o modelo SAM, mas não é necessário.
Podemos invocar nossa função localmente ou podemos
simplesmente implementar diretamente na nuvem.
Portanto, o Sam tem uma instalação de teste local que você pode
usar, mas vamos direto para a implementação.
Portanto, faremos a implantação do SAM menos, menos guiada,
e isso implantará o SAM na função Lambda.
Então vamos lá.
Portanto, para o nome da pilha, vou deixá-lo como aplicativo SAM.
A região, eu a deixarei como padrão.
Queremos mostrar os recursos a serem implantados e
confirmá-los com um Y?
Sim, vou dizer que sim.
Precisamos de permissões para criar recursos?
Sim, crie uma criação de função SAM CLI IAM.
Desejamos desativar a reversão? Não, está tudo bem.
Não precisamos desativar a reversão.
Não tem autenticação, está tudo bem? Sim, isso é bom.
Salvar argumentos no arquivo de configuração.
Sim, dessa forma, não precisaremos fazer isso novamente.
E este é o arquivo de configuração.
Portanto, sim, o nome do ambiente é padrão, e agora estamos
prontos para começar.
Portanto, agora ele criará os recursos necessários
e implementará nossas funções Lambda na nuvem.
Portanto, podemos
dar uma olhada nisso acessando o CloudFormation, aqui.
E, como você pode ver, neste momento, estamos
implantando uma pilha padrão gerenciada pela CLI
do SAM, e isso criará alguns
recursos para o SAM, como um
bucket S3 e uma função IAM.
Portanto, vou criar um pouco,
se eu esperar um pouco.
E agora, como esse modelo foi concluído, estamos
prontos, e agora temos um novo
conjunto SAM, que é a pilha real do nosso aplicativo Lambda SAM.
Então, ele diz que vou adicionar todas essas
coisas, como uma permissão do Lambda, uma função do IAM, uma função
do Lambda, um gateway de API e assim por diante.
Portanto, diremos que sim, por favor, faça.
E agora vamos receber as atualizações do CloudFormation
diretamente nesta janela, mas você também pode
acompanhá-las, se quiser, na interface do usuário
diretamente do CloudFormation.
Portanto, agora vamos aguardar a implantação de tudo.
E agora nossa função está implantada,
portanto, como podemos ver, temos um gateway de API e uma função Hello World
foi implantada.
Portanto, se você acessar o Lambda agora e atualizar isso, e eu apenas
filtrar o SAM, teremos uma função Hello World.
Portanto, essa função foi a função que foi
implantada em nosso código.
Então, aqui está o aplicativo. py.
Esse é o código que tínhamos antes.
Portanto, ele foi totalmente implantado e, além disso,
se acessarmos o gateway de API para esses modelos
específicos, poderemos
ver que temos uma API de aplicativo SAM.
Aqui está o recurso GET e,
portanto, ele invocará nossa função Lambda, como
você pode ver aqui.
Portanto, isso é ótimo. Assim, podemos testá-lo.
Por exemplo, aqui
temos um endpoint de produção que podemos testar.
Então, vou copiar esse valor, acessar meu
navegador da Web e executá-lo. Recebo
como resposta, e escrevi, a mensagem
"Hello world", que é muito útil, e também posso
fazer isso no Mass CLI aqui.
Então, faço o curl e depois o URL e recebo
a mensagem "Hello world". Portanto, é um aplicativo
de demonstração muito simples,
mas, como você pode ver, usando apenas
a CLI do SAM e configurando alguns arquivos,
conseguimos implantar um aplicativo sem servidor completo
com uma função e um gateway de API, o que é incrível,
eu diria.
E, é claro, você provavelmente teria esse código em seus
computadores e, em seguida, criaria o aplicativo completo
usando a CLI do SAM e o implantaria ao longo do tempo.
Portanto, há muito mais que você pode
ver no SAM, mas esse é o nosso 101, eu diria.
Espero que tenham gostado
e nos veremos na próxima palestra.
