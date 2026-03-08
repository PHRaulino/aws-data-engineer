e estamos no console do API Gateway.
Portanto, como você pode ver aqui, tenho a
opção de escolher um tipo de API.
Portanto, temos APIs HTTP, APIs WebSocket,
API REST,
que são públicas ou privadas e, portanto,
trataremos
apenas de uma API REST por enquanto.
Portanto, podemos experimentar o novo
console clicando
nele, que será o padrão em breve.
Portanto, certifique-se de ter isso.
Em seguida, você escolhe a API REST e a
constrói.
Portanto, quando você cria uma API,
uma API REST, tem várias opções.
Você pode criar uma nova API ou importar
uma
de um arquivo de definição de API aberto.
Então, onde está escrito arquivo, basta
importar
e a API é criada para você.
Você pode clonar uma API existente ou
começar com a API de exemplo.
Para nós, começaremos com uma nova
API e o nome será MyFirstAPI.
Agora, como você pode ver no tipo
de endpoint da API, temos três opções.
Temos Regional, otimizado para Edge ou
Private.
Portanto, o Regional será implantado em
uma região.
A otimização de borda será implantada
em muitas regiões diferentes, mas é
na borda que será implantada.
E depois, a API ainda viverá em uma
região.
Ou privado é apenas privado, não exposto à
Web.
Para simplificar as coisas, vou escolher
o tipo de API regional.
Então, vou criar a API.
E aqui estamos nós.
Então, agora que estamos aqui, vamos
criar nosso primeiro método nessa API.
Para isso, você clica em criar método aqui
e, em seguida, escolhe o tipo de método.
Portanto, poderia ser qualquer um desses
verbos HTTP, mas
faremos um GET apenas para obter uma
página.
Em seguida, você deve escolher o tipo de
integração.
Portanto, você pode ver que temos cinco
opções.
Temos função Lambda, HTTP, Mock,
serviço AWS e link VPC.
E a que estaremos testando é a função
Lambda.
Mas quero mostrar a você que também
podemos
nos integrar a qualquer serviço em
qualquer região.
Assim, escolhemos uma região e, em
seguida, escolhemos um serviço.
E o que ele faz é expor
alguns dos seus serviços do AWS como
uma API por meio do API Gateway.
Portanto, vamos manter as coisas simples e
usar as funções Lambda neste caso.
Portanto, precisamos escolher uma função
Lambda, mas
para isso, é claro, precisamos criá-la.
Então, vamos para o Lambda e criamos nossa
função que reagirá a esse gateway de API.
Portanto, crie uma função e
eu a chamo de api-gateway-route-gets.
E isso é perfeito.
E a estrutura que usarei no tempo
de execução será o Python 3.11, mas
qualquer Python 3 ou Python deve
funcionar.
Portanto, isso é perfeito.
Vamos criar essa função.
E enquanto isso está sendo criado, quero
mostrar o código que vamos usar.
Então, estou em meu código, em minha
pasta e lá está o lambda-code.py.
E este é todo o código que vamos copiar
para o Lambda.
Portanto, a ideia é que essa função
seja muito simples e responda a um
evento com algum contexto e diga: "Ei,
o corpo será hello do Lambda.
Ele será retornado como o corpo".
O código de status é 200.
E os cabeçalhos são Content-Type
application/json,
para que o navegador da Web
saiba que recebemos uma resposta JSON.
Então, vou copiar todo esse código.
Role a tela para baixo e cole-a aqui.
Portanto, vamos implementar essa função.
Então, vou clicar em Deploy para
implementar
essa função e também podemos testá-la.
Assim, por exemplo, posso criar um evento
de teste chamado DemoTest.
Em seguida, enviamos esse evento, o
salvamos e clicamos em Testar.
E, como você pode ver, o resultado é
hello do Lambda com código de status 200.
Portanto, tudo está funcionando bem no
momento e isso é perfeito.
E o que vou fazer agora é integrar
essa função Lambda ao meu gateway de API.
Então, aqui dentro, vou copiar o ARN da
função, acessar meu
gateway de API e, em seguida, clicar e
colar o ARN.
Perfeito.
Portanto, agora temos a função do Lambda
integrada e, como
queremos ver as solicitações completas que
estão sendo passadas
para o Lambda e enviadas de volta pelo
Lambda,
você vai usar a integração do proxy do
Lambda.
Agora, quanto ao tempo limite, como você
pode
ver, embora uma função Lambda possa ter um
tempo limite longo, por exemplo, cinco
minutos ou
15 minutos, o API Gateway tem um tempo
limite limitado e o padrão é 29 segundos.
Você pode personalizá-lo e deixá-lo menor
que 29 segundos, mas
o tempo limite padrão é de 29 segundos,
independentemente do
tempo que a função Lambda leva para ser
executada.
Portanto, vamos criar esse método e ele
concederá automaticamente ao gateway da
API o
direito de invocar nossa função Lambda.
Portanto, se eu voltar aqui e atualizar
esta página, como você pode ver, agora
nosso gateway de API pode invocar nossa
função Lambda e podemos verificar isso
acessando
a configuração e depois as permissões.
E se dermos uma olhada na declaração de
política baseada em recursos, esta aqui, e
clicarmos
em Exibir política, veremos que meu
gateway de
API tem permissão para invocar minha
função Lambda
se a API de origem for a do
meu gateway de API com rota GET.
Portanto, esse é o material que acontece
nos bastidores do AWS
para permitir que o gateway de API invoque
nossa função Lambda.
Portanto, sabemos que tudo é feito a
partir de uma perspectiva de segurança.
Portanto, agora podemos dar uma olhada no
nosso gateway de API.
Portanto, o cliente desse método envia uma
solicitação e
podemos dar uma olhada na própria
solicitação aqui.
Portanto, todas as configurações estão
aqui, a integração é
feita com o Lambda e, portanto, é um
tipo de integração do Lambda com proxy
ativado.
Então, o próprio Lambda é essa função.
Podemos clicar nele e voltar à nossa
função.
Então, a resposta é a integração do proxy.
Isso significa que o gateway de API
analisará o
que está sendo enviado pelo Lambda e o
interpretará.
E a resposta do método é o que temos aqui.
Poderíamos modificá-lo se você quisesse,
mas estamos procurando por
application/json.
Então, vamos testar essa API.
Portanto, para isso, no canto inferior
direito, há um
teste e você pode especificar algumas
cadeias de
consulta ou alguns cabeçalhos, mas não
especificamos nada.
Basta clicar em Test.
E o teste é: ei, o corpo
da resposta é hello do Lambda.
Portanto, você pode ver no gateway da API
que o status é 200.
Isso vem diretamente do nosso código aqui,
que diz que o status é 200.
Também temos o corpo da resposta, hello
from
Lambda, que, novamente, foi definido em
nosso
código bem aqui, body igual a json.dumps.
E então, olá da Lambda.
E, por fim, o tipo de conteúdo é JSON,
e isso é recuperado como parte dos
cabeçalhos de
resposta que são do tipo de conteúdo JSON.
Além disso, a partir do teste, podemos dar
uma
olhada no registro de execução do gateway
de API,
o que é muito bom, pois também é quando
você quer depurar e ver o que está
acontecendo.
Uma maneira muito agradável de fazer isso.
Portanto, fizemos nossa primeira execução
de um gateway
de API com base em uma função Lambda.
Então, agora vamos depurar isso e ver o
que
está sendo enviado para a nossa função
Lambda.
Então, farei o evento de impressão
e, em seguida, implantarei isso e
invocaremos nossa função Lambda novamente
a
partir do gateway de API.
Então, vamos executar um novo teste, que
ainda diz olá do Lambda, mas
desta vez estamos imprimindo os eventos.
Portanto, se acessarmos os registros
do CloudWatch, devemos conseguir
encontrá-lo.
Então, vamos entrar no monitoramento e
examinar os registros do CloudWatch.
Vamos encontrar o fluxo de registro mais
recente, este aqui.
E aqui temos nosso registro.
E podemos ver aqui que esse foi
o evento impresso recebido do API Gateway.
Então, algumas informações que você tem
aqui, por exemplo, o
recurso que é barra, o caminho barra, o
método
que é GET, e então você obtém cabeçalhos e
parâmetros de string de consulta e assim
por diante.
Portanto, muitas informações são
transmitidas pelo gateway
da API para nossa função Lambda.
E nossa função Lambda pode usar essas
informações para forjar
uma resposta e enviá-la de volta ao
gateway da API.
Portanto, agora podemos ir em frente e
criar um novo recurso.
Portanto, desta vez, teremos o recurso
fazendo isso
e o nome do recurso será houses.
Então, vamos criar esse recurso.
E agora temos o caminho /houses que acabei
de abrir.
E em /houses, vou criar um método.
Será um GET novamente para a
função Lambda de integração de proxy.
E preciso criar minha função Lambda.
Então, vamos fazer isso rapidamente, vou
copiar isso e criar uma função.
E ainda não é raiz, são casas ainda.
O tempo de execução ainda será Python.
E vamos criar essa função.
Mais uma vez, vou apenas copiar esse
código.
Assim, em vez de hello from Lambda,
vamos alterar a mensagem para hello from
e, em seguida, algo com houses.
Portanto, minha função foi criada.
Vamos copiar isso e vamos dar
um alô da minha linda casa.
Muito bem, vamos implementar isso.
Portanto, agora implantamos a função.
Vou copiar a função
ARN e colá-la aqui.
E crie esse método.
Portanto, agora temos /houses que tem o
método GET.
Posso testar isso.
Então, vamos testá-lo e clicar em Test.
E, como você pode ver, recebo 200
cumprimentos da minha linda casa.
E até agora está muito legal.
Temos a raiz, GET, e temos as casas,
GET, que invocam duas funções Lambda
diferentes.
Mas queremos poder acessar isso em um
navegador da Web, e
não apenas testá-lo na interface do
usuário do API Gateway.
Então, vamos clicar em Deploy API e
precisamos selecionar um estágio.
Portanto, será um novo estágio, e o nome
é dev, daremos uma olhada nele mais tarde.
Vamos implantar isso.
E agora que implantamos essa API, há um
URL de invocação.
Então, vou copiar esse URL e
colá-lo em meu navegador da Web.
E, como você pode ver, quando vou
para /dev, ele diz olá do Lambda.
Portanto, este é apenas o Firefox fazendo
uma impressão
bonita, mas você recebe um alô do Lambda.
E se eu for para /houses, receberei
um alô da minha linda casa.
Portanto, essa API tem duas funções Lambda
respondendo a mim.
E se eu fizer algo errado, se eu
fizer /wrong, estou recebendo uma mensagem
de erro,
como mensagem de token de autenticação
ausente.
Então vamos lá.
Implantamos nossa API no API Gateway
e isso é muito legal porque,
bem, temos duas funções Lambda nos
bastidores que realmente respondem a ela.
E isso é tudo para nossa função básica no
API Gateway.
Espero que tenham gostado e nos veremos na
próxima palestra.
