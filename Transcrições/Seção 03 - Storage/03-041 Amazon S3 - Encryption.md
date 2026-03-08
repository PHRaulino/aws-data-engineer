Agora, vamos falar sobre a criptografia
Portanto, você pode criptografar objetos em buckets do S3 usando
um dos quatro métodos a seguir.
A primeira é a criptografia no lado do servidor, SSE, e há
vários tipos dela.
Portanto, você tem o SSE-S3, que é a criptografia
do lado do servidor com chaves gerenciadas pelo Amazon S3, e que é
ativada por padrão para seus
buckets e objetos.
Em seguida, temos o SSE-KMS, em que criptografamos dessa vez com uma
chave KMS para gerenciar a chave de criptografia.
Em seguida, temos o SSE-C para usar a chave fornecida pelo cliente, portanto,
desta vez, fornecemos a própria chave de criptografia.
E não se preocupe, veremos tudo isso
em detalhes no próximo slide, portanto,
esta é apenas uma visão geral.
E temos a criptografia no lado do cliente quando queremos
criptografar tudo no lado do cliente
e depois fazer o upload para o Amazon S3.
Portanto, no exame, é importante entender
quais são para cada situação, por
isso vamos nos aprofundar em todos
eles e entender suas especificidades.
Portanto, o primeiro é o Amazon S3 para criptografia SSE-S3.
Portanto, nesse caso, a criptografia está usando uma chave
que é manipulada, gerenciada e de propriedade da AWS.
Você nunca tem acesso a essa chave.
O objeto será criptografado no servidor pelo AWS
e o tipo de segurança da criptografia é AES-256.
Portanto, você deve definir
o cabeçalho como "x-amz-server-side-encryption": "AES256" para solicitar
que o Amazon S3 criptografe o objeto
para você usando o mecanismo SSE-S3.
Agora o SSE-S3 está ativado por padrão
para novos buckets e novos objetos.
Então, como isso funciona?
Temos o Amazon S3 e temos nosso usuário.
O usuário, você, fará o upload de um arquivo com
o cabeçalho correto e, em seguida,
ele será um objeto no Amazon S3.
O Amazon S3 fará o pareamento com a chave de propriedade do S3, pois
estamos usando o mecanismo SSE-S3.
Em seguida, realizaremos a criptografia
misturando a chave e o objeto, e isso será
o que será armazenado em seus buckets do S3.
Portanto, esse é o mais simples, o SSE-S3.
Em seguida, temos o SSE-KMS.
Portanto, desta vez, em vez de confiar
na chave de propriedade da AWS e do serviço S3, você
deseja gerenciar suas próprias chaves usando
o serviço KMS, o Key Management Service.
Portanto, a vantagem de usar o KMS é que
você tem o controle do usuário sobre essa
chave, de modo que você mesmo pode criar chaves no KMS e pode
editar o uso da chave usando o CloudTrail.
Portanto, sempre que alguém usar uma chave no KMS, isso
será registrado em um serviço que
registra tudo o que acontece no AWS chamado CloudTrail.
Portanto, para isso, precisamos ter um cabeçalho chamado "x-amz-server-side-encryption":
"aws:kms" e, em seguida, o objeto será criptografado no lado do servidor.
Portanto, qualquer coisa SSE, é claro, é do lado do servidor.
Então, como isso funciona?
Bem, novamente, carregamos o objeto,
desta vez com um cabeçalho diferente
e, no cabeçalho, especificamos
a chave KMS que queremos usar.
Em seguida, o objeto está aparecendo no
Amazon S3 e, desta vez, a chave KMS que
será usada está saindo do AWS KMS.
Portanto, essas duas coisas juntas serão combinadas
e, em seguida, você obterá criptografia,
e o arquivo acabará nos buckets do S3.
Portanto, agora, para ler esse arquivo do bucket
do S3, você precisa não apenas acessar o objeto em si,
mas também a chave KMS subjacente que foi usada para criptografar
esse objeto.
Portanto, esse é outro nível de segurança.
Portanto, o SSE-KMS tem algumas limitações
porque, embora agora você faça upload
e download de arquivos do Amazon S3, é necessário
utilizar uma chave KMS.
A chave KMS tem suas próprias APIs,
por exemplo, GenerateDataKey,
e quando você descriptografar, usará a API Decrypt
e, portanto, fará chamadas de API para o serviço KMS.
Cada uma dessas chamadas de API será contabilizada
nas cotas de chamadas de API do KMS por segundo, portanto, com base
na região, você terá
entre 5.000 e 30.000 solicitações por segundo, embora elas
possam ser aumentadas usando o Console
de cotas de serviço.
Portanto, se você tiver um bucket S3 de taxa de transferência muito alta e tudo
estiver criptografado usando chaves KMS, poderá
entrar em um caso de uso do tipo thread link.
Portanto, isso é algo que o exame pode testar em você.
Em seguida, temos o tipo de criptografia SSE-C.
Portanto, desta vez, as chaves são gerenciadas fora do AWS, mas ainda
é uma criptografia no lado do servidor
porque enviamos a chave para o AWS.
Mas o Amazon S3 nunca armazenará a chave de
criptografia que você fornecer.
Depois de usados, eles são descartados.
Portanto, nesse caso, como transmitimos uma chave para o
Amazon S3, precisamos usar HTTPS e passar a chave como
parte dos cabeçalhos HTTP para cada solicitação feita.
Então, como isso funciona?
O usuário fará o upload de um arquivo e da chave, mas gerenciará
a chave fora do AWS.
Em seguida, o Amazon S3 usará a chave fornecida pelo cliente
e o objeto para executar alguma criptografia e, em seguida,
colocará o arquivo criptografado em um bucket do S3.
E, é claro, para ler esse arquivo, o
usuário deve fornecer novamente a chave
que foi usada para criptografar esse arquivo.
Por fim, temos a criptografia no lado do cliente.
Portanto, isso é mais fácil de implementar
se aproveitarmos alguma biblioteca
de cliente, como a Client-Side Encryption Library.
E a ideia da criptografia do lado
do cliente é que os próprios clientes devem criptografar
os dados antes de enviá-los ao Amazon S3.
Além disso, você pode recuperar os dados do Amazon
S3 e, em seguida, a descriptografia
dos dados ocorre no cliente fora do Amazon S3.
Portanto, os clientes gerenciam totalmente as
chaves e o ciclo de criptografia.
Então, como isso funciona?
Temos um arquivo e a chave de um cliente
que está fora do AWS.
O próprio cliente fornecerá e executará
a criptografia, portanto,
agora temos um arquivo criptografado,
e esse arquivo pode ser enviado para o Amazon S3 para upload.
Portanto, já vimos todos os níveis de criptografia de objetos, mas
agora vamos falar sobre criptografia em trânsito.
Portanto, a criptografia em trânsito, ou
em voo, também é chamada de SSL ou TLS e, basicamente,
seu bucket do Amazon S3 tem dois pontos de extremidade, o ponto
de extremidade HTTP que não é criptografado e o ponto
de extremidade HTTPS que tem criptografia em voos.
Portanto, sempre que você visita
um site e vê esse cadeado verde, geralmente
isso significa que ele está usando criptografia em
voos, ou seja, a conexão entre você e o servidor
de destino é segura e totalmente criptografada.
Portanto, quando você estiver
usando o Amazon S3, é totalmente recomendável
usar HTTPS para ter uma transmissão segura
de dados, é claro, e se você usar o mecanismo do tipo SSE-C,
deverá usar o protocolo HTTPS.
Isso não é algo com que se preocupar
na vida real, pois a maioria dos clientes
usaria o endpoint HTTPS por padrão.
Como você faria para forçar a criptografia nos trânsitos?
Para isso, poderíamos usar uma política de balde.
Portanto, você anexa uma política de bucket
ao seu bucket S3 e anexa esta declaração
que diz que você nega qualquer operação GetObject
se a condição for "aws:SecureTransport": "false".
Portanto, SecureTransport será verdadeiro sempre que você usar
HTTPS e falso sempre que não estiver usando uma criptografia,
uma conexão criptografada
e, assim, qualquer usuário que tentar usar HTTP no
seu bucket será bloqueado, mas
os usuários que usarem HTTPS poderão ser permitidos.
Ok, então é isso para a criptografia,
espero que tenham gostado e nos vemos na próxima palestra.
