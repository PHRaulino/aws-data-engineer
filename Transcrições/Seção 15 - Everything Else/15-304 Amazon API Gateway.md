sem servidor, vimos como criar funções
Lambda e como usar o DynamoDB.
Assim, as funções podem usar o DynamoDB
como um banco de dados para nossa API, e podemos criar, ler,
atualizar e excluir nossas tabelas, mas
gostaríamos que nossos clientes pudessem invocar
essa função Lambda de alguma forma.
Portanto, há várias maneiras de fazer isso.
Podemos fazer com que o cliente invoque diretamente a função Lambda,
mas isso significa que o cliente precisaria de permissões do
IAM, ou vimos que podemos usar um balanceador de
carga de aplicativo para ficar entre o cliente e a função
Lambda, o que exporia nossa função Lambda como
um endpoint HTTP.
Há uma última coisa que podemos usar.
Ele é chamado de API Gateway.
E essa é uma oferta sem servidor da AWS que
nos permite criar APIs REST que serão públicas
e acessíveis para nossos clientes.
Portanto, o cliente se comunicará com o
API Gateway e, o que é ótimo, o API Gateway
fará o proxy da solicitação para nossas funções Lambda.
Portanto, ele usaria um API Gateway
porque ele nos fornece mais do que apenas um endpoint HTTP.
Ele nos fornecerá vários
recursos, como veremos nesta
seção, como autenticação, planos de uso, estágios de desenvolvimento
e todos esses tipos de coisas.
Portanto, o API Gateway tem muitos recursos e esta
é apenas uma visão geral, mas podemos
integrar o API Gateway e o Lambda, o que nos dá um aplicativo
sem servidor completo.
Portanto, não há infraestrutura para gerenciar.
Temos suporte para o protocolo WebSocket
para que possamos fazer streaming em
tempo real por meio do API Gateway de duas maneiras diferentes.
O API Gateway manipula o controle de versão da API.
Assim, podemos passar da versão um para a versão
dois e para a versão três sem prejudicar nossos clientes.
Podemos lidar com vários ambientes que incluem
um ambiente de desenvolvimento, um de teste e um de produção.
Há toda uma série de questões sobre API Gateway e segurança.
Portanto, há várias maneiras de ativar
a segurança em seu API
Gateway para autenticação e autorização.
Podemos criar chaves de API, limitar as solicitações
caso alguns clientes estejam fazendo muitas
solicitações em nosso API Gateway, e também podemos
usar alguns padrões comuns, como Swagger ou Open
API 3. 0 para importar
APIs definidas rapidamente, e também podemos
exportá-las como Swagger e Open API.
Podemos transformar e validar solicitações
e respostas no nível do API
Gateway para garantir que a invocação esteja
correta e podemos gerar especificações de SDK e API e armazenar
em cache as respostas da API.
Portanto, muitos recursos que vêm com o API Gateway não
são necessariamente incluídos quando
você usa algo tão simples como um
balanceador de carga de aplicativos.
Então, com o que o API Gateway se integra?
Bem, há uma função Lambda e vimos
isso no diagrama anterior, portanto, ela
pode invocar uma função Lambda.
E, com essa integração, é a maneira mais comum e muito
fácil de expor uma API REST com o apoio de uma função
Lambda para criar um aplicativo
totalmente sem servidor.
Mas também HTTP.
Portanto, podemos expor qualquer ponto de extremidade HTTP no backend.
Portanto, pode ser, por exemplo,
uma API HTTP que você tem no local ou um balanceador
de carga de aplicativos que você
tem em seu ambiente de nuvem.
E por que você faria isso?
Bem, você usaria um API Gateway para aproveitar
os recursos de limitação de taxa, o armazenamento em cache, a autenticação
do usuário, as chaves de API, etc.
Portanto, é definitivamente muito útil
ter uma camada de API Gateway em cima do seu endpoint HTTP.
E, por fim, podemos usar um serviço de evidência
para expor qualquer API do AWS por meio do API Gateway.
Então, quais, por exemplo,
onde podemos iniciar um fluxo de trabalho
Step Function, podemos postar uma mensagem
no SQS diretamente de uma API Gateway.
Por que você faria isso?
Bem, porque talvez você queira adicionar autenticação,
implantar algumas APIs publicamente
ou fazer algum controle de taxa em alguns serviços da AWS.
Portanto, aqui está um exemplo do API Gateway
usado com um serviço do AWS.
Por exemplo, o Kinesis Data Streams.
Portanto, queremos que as pessoas enviem
dados para um Kinesis Data Streams,
mas de forma segura,
sem dar a elas acesso às credenciais do AWS.
Então, o que fazemos é que, entre nossos clientes
e nossos fluxos de dados do
Kinesis, teremos o API Gateway.
E os clientes enviarão uma solicitação
HTTP para o API Gateway.
E ele foi configurado para enviar as mensagens para
um Kinesis Data Streams.
E, como você pode ver nessa configuração, não gerenciamos nenhum servidor.
Em seguida, com o Kinesis
Data Stream, podemos, por exemplo,
enviar os registros para um Kinesis
Data Firehose e, por fim, colocá-los em um bucket do Amazon S3 no
formato JSON.
Assim, você começa a ver o poder do API Gateway.
Na verdade, você pode expor qualquer serviço do AWS
para o exterior por meio de um API Gateway.
Há três maneiras de implantar o API Gateway.
Isso é chamado de tipos de ponto de extremidade.
Portanto, o primeiro tipo, que é o padrão,
chama-se Edge-Optimized.
Isso é para seus clientes globais.
Isso significa que seu API Gateway
poderá ser acessado de qualquer lugar do mundo.
E, para ser eficiente, a
solicitação será roteada por
todos os locais do CloudFront Edge,
o que melhorará a latência.
Seu API Gateway ainda está apenas em uma região
onde você o criou, mas pode ser acessado com eficiência
de todos os locais do CloudFormation Edge.
Depois, há uma implantação regional.
Portanto, é nesse caso que não queremos usar
os locais do CloudFront Edge.
Portanto, é quando esperamos que todos os nossos
usuários estejam na mesma
região que criamos nosso API Gateway.
E, se quiser, você pode criar
sua própria distribuição de plataforma, o que lhe dará o mesmo resultado
de uma distribuição otimizada por
borda, mas dessa vez você terá mais controle
sobre as estratégias de localização e as próprias configurações
da plataforma.
E, finalmente, o último tipo de API Gateway que você pode fazer
é um API Gateway privado.
Portanto, desta vez não é público.
Portanto, um API Gateway privado só pode ser acessado
de dentro da sua VPC.
E ele usará endpoints de VPC de interface para suas ENIs.
E para definir o acesso ao seu API Gateway, você
pode usar uma política de recursos.
Agora, alguns comentários sobre
a segurança no topo do API Gateway.
Portanto, você pode identificar os usuários no API Gateway
de várias maneiras.
A primeira maneira é por meio das funções do IAM.
Portanto, isso é muito útil se você tiver aplicativos
internos, por exemplo, executados em instâncias
EC2, e eles quiserem acessar uma API no API Gateway,
basta usar as funções de IAM.
Se você quisesse ter usuários externos,
por exemplo, para aplicativos móveis ou aplicativos da Web,
usaria algo chamado Amazon Cognito.
Ou, se você quiser implementar sua própria lógica,
poderá fazê-lo com um autorizador personalizado.
Essa é uma função Lambda.
Além disso, você pode ter segurança HTTPS por meio
de seu próprio nome de domínio personalizado
por meio da integração com um serviço
chamado AWS Certificate Manager ou ACM.
Portanto, esse certificado, se você
estiver usando um endpoint Edge-Optimized, deverá estar em us-east-1,
mas se estiver usando um endpoint regional,
esse certificado poderá estar na mesma região
que o estágio do API Gateway.
Por fim, é preciso configurar, é claro,
um registro CNAME ou A-alias no Route 53
para apontar para o seu domínio e o API Gateway.
Então é isso para esta palestra.
Espero que você tenha gostado.
E eu o verei na próxima palestra.
