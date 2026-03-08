Portanto, o CloudWatch Logs é o local perfeito
para armazenar os registros de aplicativos no AWS.
E, para isso, você deve primeiro definir grupos de registros.
Eles têm o nome que você
quiser, mas geralmente representam um de seus aplicativos.
Em seguida, dentro de um grupo de logs, você terá vários fluxos
de logs, e eles representam instâncias de logs dentro de um aplicativo
ou arquivos de logs específicos ou contêineres específicos que você tem
como parte de um cluster.
Em seguida, defina sua política de expiração de registros.
Assim, você pode reter os logs indefinidamente
e nunca expirar, ou pode optar por expirá-los
entre um dia e 10 anos.
Também é possível enviar seus logs do CloudWatch
para vários destinos.
Por exemplo, para exportá-los em lote para o Amazon S3 ou
para transmiti-los para o Kinesis Data Streams,
Kinesis Data Firehose, AWS Lambda, Amazon OpenSearch.
Todos os logs são criptografados por padrão, e você
pode configurar sua própria criptografia baseada
em KMS com suas próprias chaves, se desejar.
Então, que tipo de dados de registros vão para o CloudWatch Logs?
Agora, que tipos de registros podem ir para o CloudWatch Logs?
Bem, podemos enviar os registros usando o SDK
ou o CloudWatch Logs Agent
ou o CloudWatch Unified Agent.
Agora, os agentes unificados do CloudWatch enviam
registros para o CloudWatch e, portanto, o agente de registro do CloudWatch está obsoleto.
Você tem o Elastic Beanstalk, que é usado para coletar
logs do aplicativo diretamente no CloudWatch.
O ECS enviará os logs diretamente dos contêineres
para o CloudWatch.
O Lambda enviará os registros das próprias funções.
Os registros de fluxo da VPC enviarão registros
específicos do tráfego de rede de metadados da VPC.
O API Gateway enviará todas as solicitações feitas
ao API Gateway para o CloudWatch Logs.
CloudTrail, você pode enviar os logs
diretamente com base no filtro.
E o Route53 registrará todas as consultas
de DNS feitas ao seu serviço.
Então, e se você quisesse consultar os registros no CloudWatch Logs?
Para isso, você pode usar o CloudWatch Logs Insights.
Portanto, é um recurso de consulta no CloudWatch Logs que permite
que você escreva sua consulta.
Você especifica o período de tempo ao qual deseja aplicar sua consulta
e, em seguida, obtém automaticamente um resultado
como visualização.
Além disso, você pode ver as linhas de registro específicas
que fizeram essa visualização.
Essa visualização também pode ser exportada como
um resultado ou adicionada a um painel para que possa
ser executada novamente sempre que desejar.
Isso é muito útil e permitirá
que você pesquise e analise dados de registro
no CloudWatch Logs.
Portanto, há muitas consultas simples fornecidas
como parte do console do CloudWatch Logs Insights.
Por exemplo, você pode encontrar os 25 eventos mais recentes,
ou pode verificar
quantos eventos tiveram exceções ou erros nos logs, ou pode
procurar um IP específico e assim por diante.
Portanto, ele fornece uma linguagem de consulta criada para fins específicos.
Todos os campos que permitem que você crie suas consultas são
detectados automaticamente nos logs do CloudWatch e, em seguida, você
pode filtrar com base nas condições.
Você pode calcular estatísticas agregadas,
classificar eventos, limitar o número de eventos e assim por diante.
Portanto, como eu disse, você pode salvar as consultas
e também adicioná-las aos painéis do CloudWatch.
E você tem a capacidade de consultar vários grupos de registros
ao mesmo tempo, mesmo que estejam em contas diferentes.
Portanto, lembre-se de que o CloudWatch Logs Insights é um mecanismo de consulta,
não um mecanismo em tempo real.
Portanto, como tal,
ele só consultará dados históricos quando você executar a consulta.
Portanto, conforme mencionado,
os registros do CloudWatch podem ser exportados para vários destinos.
O primeiro é o Amazon S3.
Portanto, trata-se de uma exportação em lote para
enviar todos os seus registros
para o Amazon S3, e essa exportação pode levar até 12 horas para ser concluída.
A chamada de API para iniciar essa exportação é chamada
CreateExportTask.
Portanto, como se trata de uma exportação em
lote, não é em tempo real ou quase em tempo real.
Em vez disso, você deve usar a assinatura do CloudWatch Logs.
Assim, eles permitem que você obtenha um fluxo em tempo real
desses eventos de registro, e você pode fazer o processamento e a análise.
Assim, você pode enviar esses dados para vários locais,
como o Kinesis Data Streams, o Kinesis Data Firehose
ou o Lambda.
E você pode especificar um filtro de assinatura para dizer que tipo
de eventos de log você deseja que sejam entregues ao seu destino.
Portanto, o filtro de assinatura pode enviar dados
para os fluxos de dados do Kinesis.
Essa seria uma ótima
opção se você quisesse
usar, por exemplo, a integração com o Kinesis Data Firehose,
o Kinesis Data Analytics, o Amazon EC2 ou o Lambda.
Você também pode enviá-lo diretamente para o Kinesis Data Firehose.
A partir daí, você pode enviá-lo quase em tempo
real para o Amazon S3 ou, por exemplo,
para o OpenSearch Service, ou para o Lambda.
Portanto, você pode escrever sua própria função
Lambda personalizada ou usar uma função Lambda gerenciada
que esteja enviando dados em tempo real para o OpenSearch Service.
Além disso, graças a esses filtros de assinatura,
é possível agregar dados de diferentes
logs do CloudWatch em diferentes contas e
regiões em um destino comum, como o fluxo de dados
do Kinesis em uma conta específica.
E depois o Kinesis Data Firehose.
E depois, quase em tempo real, no Amazon S3.
Portanto, isso é muito
possível e é uma maneira de realizar a agregação de logs.
Portanto, a essência de como isso funciona
é que você deve usar o que chamamos de destinos.
Então, digamos que você tenha uma conta de remetente
e as contas de destinatário.
Portanto, você cria um filtro de assinatura do CloudWatch
Log e, em seguida, ele é enviado para um destino de assinatura,
que é um representante virtual do fluxo
de dados do Kinesis nas contas do destinatário.
Em seguida, você anexa uma política de acesso ao
destino para permitir que a primeira conta realmente
envie dados para esse destino.
Em seguida, crie uma função de IAM na conta do destinatário,
que tem permissão para enviar registros
para o seu Kinesis Data Stream, e certifique-se
de que essa função possa ser assumida pela primeira
conta.
E quando todas essas coisas
estiverem prontas,
será possível enviar dados do CloudWatch
Logs de uma conta para um destino em outra conta.
Então é isso para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
