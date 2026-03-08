em todos os serviços da AWS que vimos até agora.
Isso vai ser longo e entediante, mas, acredite,
é praticamente necessário para o exame, então vamos começar.
Primeiro, o Kinesis é composto pelos fluxos de dados do Kinesis.
E o Kinesis Data Streams tem SSL Endpoints para que possamos
usar o protocolo HTTPS e fazer a criptografia em voo, o que
significa enviar os dados para o Kinesis de forma segura.
Há também a integração do KMS para fornecer criptografia no lado
do servidor, o que nos proporciona criptografia em repouso.
Além disso, podemos fazer a criptografia do lado do cliente, mas precisamos
usar nossas próprias bibliotecas de criptografia.
Não há suporte para isso no serviço Kinesis e precisaremos
usar a KPL, a Biblioteca do Produtor, para fazer isso,
mas também precisaremos fornecer a criptografia por
conta própria.
Há uma interface compatível com Endpoints de VPC, Private
Link, o que significa que podemos acessar o
serviço Kinesis em nossas instâncias privadas do EC2 de forma privada.
Podemos usar o KCL para ler do Kinesis, mas lembre-se de que, se você
usar o KCL para ler do Kinesis Streams, também
deverá conceder acesso de leitura e gravação a uma tabela
do DynamoDB.
Por quê?
Porque esse KCL usará a tabela do DynamoDB para fazer
o checkpointing e compartilhar o trabalho entre diferentes
instâncias do KCL.
Portanto, lembre-se disso.
Agora, para o Kinesis Data Firehose, anexamos funções de IAM para
que possamos fornecer dados ao S3, ElasticSearch, Redshift
e Splunk.
Esperamos que você se lembre desses quatro destinos.
E, além disso, todo o fluxo de entrega pode ser criptografado
usando o KMS, que é a criptografia do lado do servidor.
Também há suporte para Endpoints VPC e Links Privados
para acesso privado.
Por fim, para o Kinesis Data Analytics, podemos
anexar uma função IAM a ele para que possa ler os fluxos de dados
do Kinesis de que precisamos.
E faça referência às fontes, talvez para dados de referência.
E gravar uma saída em um destino de saída, por exemplo,
o destino de saída pode ser o Kinesis Streams ou
o Kinesis Firehose.
Então é isso para toda a segurança do Kinesis.
Vamos para a próxima tecnologia.
A próxima tecnologia é o SQS.
O SQS nos fornecerá criptografia em voo usando o HTTPS Endpoint,
para que possamos transferir dados para o SQS com segurança.
Também teremos criptografia no lado do servidor usando o KMS.
E você deve definir uma política de IAM para permitir o uso do SQS.
Há também um segundo nível de segurança que podemos definir
usando as políticas de acesso à fila do SQS e garantindo que nossos usuários
tenham acesso ao serviço SQS.
Isso é muito semelhante, por exemplo, a uma política de bucket do S3.
Se você quiser fazer a criptografia no lado
do cliente, como de costume, deverá fazê-la manualmente e por
conta própria.
Isso não é algo suportado diretamente
pelo serviço.
E você obtém um VPC Endpoint que é fornecido
para uma interface, caso queira acessar o serviço SQS
com segurança.
Muito bem, a seguir.
O próximo é o AWS IoT.
A IoT tem muitos títulos diferentes, não sei
se você se lembra, mas o primeiro deles são as políticas.
Basicamente, vamos criar o X. 509 ou identidades
Cognito em nossos dispositivos.
E usando as políticas de IoT, podemos controlar tudo.
Podemos revogar qualquer dispositivo a qualquer momento.
E as políticas de IoT são documentos JSON,
assim como as políticas de IAM.
Elas podem ser anexadas a grupos em vez de coisas individuais, de modo
que podemos basicamente agrupar as coisas
e apenas gerenciar políticas de grupos em vez de políticas de coisas.
Isso foi para a segurança do Things, mas podemos
obter políticas de IAM para analisar o acesso dos usuários, grupos
ou funções no serviço de IoT.
Portanto, podem ser políticas de IAM associadas a usuários, grupos
ou funções e insights.
E, então, você pode basicamente usar isso para controlar
o acesso à IoT, APIs em alto nível, por exemplo, criando
uma regra ou uma ação real, esse tipo de
coisa.
Em seguida, você anexa as funções ao Rules Engine, para
que elas possam executar suas ações.
Portanto, se a ação do Rules Engine estiver enviando dados para o Kinesis,
você precisará anexar uma função de IAM a essa regra, basicamente,
para que ela possa executar uma ação atualizada e enviar dados
de fato para o Kinesis.
Está bem.
Agora, o S3, já vimos isso muitas vezes, a segurança do S3,
mas mais uma vez.
Temos políticas de IAM, políticas de bucket S3, listas
de controle de acesso, criptografia em voo usando HTTPS, criptografia
em repouso de vários tipos diferentes.
Temos criptografia no lado do servidor, SSE-S3, SSE-KMS, SSE-C.
Obtemos criptografia no lado do cliente, como os clientes de criptografia
do Amazon S3.
Além disso, temos o controle de versão e a exclusão de MFA
basicamente para garantir que os dados não sejam excluídos por engano.
Podemos obter CORS para proteger sites e garantir
que apenas alguns sites tenham acesso ao nosso bucket S3.
Temos o VPC Endpoint que é fornecido por meio
de um Gateway Endpoint, basicamente para acessar o S3 com segurança a partir
da minha sub-rede privada.
E temos o Glacier, acabei de incluir o Glacier aqui, que
tem um monte de coisas, mas incluindo essas coisas
chamadas políticas de bloqueio de cofre que são
muito úteis se você quiser impedir exclusões, por exemplo, por motivos regulatórios,
e isso também é chamado de política WORM, Write
Once Read Many.
Agora vamos falar sobre a segurança do DynamoDB.
Portanto, os dados serão criptografados em trânsito
usando TLS ou HTTPS.
E todas as suas tabelas do DynamoDB serão
criptografadas em repouso.
Ele usará a criptografia KMS para tabelas básicas e
índices secundários, e você tem três opções.
A primeira é usar a chave padrão de propriedade da
AWS, que é gratuita.
A segunda opção é usar uma chave gerenciada pelo
AWS, que é, por exemplo, aws/dynamodb, o que incorrerá em algumas
cobranças de KMS.
Ou a última é ter uma chave gerenciada pelo cliente da AWS, a sua
própria, certo?
E você também terá os encargos do KMS para isso.
Agora, todo o acesso às tabelas do DynamoDB, à API
e ao DynamoDB DAX Cluster sempre será autenticado e autorizado
usando as políticas do IAM.
Agora, se você habilitar os fluxos do DynamoDB, eles
também serão criptografados com o mesmo mecanismo
de criptografia da tabela do DynamoDB.
E se você quiser acessar a tabela do DynamoDB de forma
privada, poderá usar o VPC Endpoint,
que será fornecido por meio de um Gateway.
Então é isso para esta palestra, espero que você tenha gostado.
E eu o verei na segunda parte para obter mais segurança
em outros serviços.
