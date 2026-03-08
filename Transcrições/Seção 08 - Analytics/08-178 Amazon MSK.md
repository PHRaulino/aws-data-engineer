Agora vamos falar sobre
no exame de especialidade em análise de dados.
Você não precisa saber como usar o Kafka, porque, na verdade,
é bastante complicado usar o Kafka.
Portanto, não haverá aulas práticas
sobre isso, mas você precisa saber como o MSK funciona,
qual é a arquitetura e as diferenças em relação ao Kinesis.
Portanto, o Kafka é uma alternativa ao Kinesis, e haverá uma
palestra dedicada ao Kafka
versus Kinesis na próxima palestra.
Porque o exame tentará principalmente fazer você escolher
entre o Kafka e o Kinesis com base em algum cenário.
Mas o que é Kafka e MSK?
Portanto, o MSK é um serviço Apache Kafka totalmente gerenciado no AWS, que permite
criar, atualizar e excluir
clusters do Kafka.
E, nesse caso, o
Amazon MSK criará e gerenciará os nós do broker Kafka
e do Zookeeper para você.
Você implementa seu cluster MSK em sua VPC,
ele é multi-AZ até três para alta disponibilidade.
Há recuperação automática
de falhas comuns do Apache Kafka, e os
dados são armazenados em volumes EBS.
A ideia é que o MSK e o Kafka substituam o Kinesis, onde você
tem, da mesma forma, seus
produtores e seus consumidores de dados.
Mas o poder do Kafka é que você pode criar algumas
configurações personalizadas para o seu cluster.
Por exemplo, um exemplo que pode aparecer
no exame é que, por padrão, o tamanho da mensagem
é de um megabyte no Apache Kafka.
Mas você pode configurar o Apache Kafka para enviar e receber mensagens grandes,
por exemplo, de até 10 megabytes em
seu cluster, depois de fazer algumas configurações
personalizadas.
E essa é uma grande diferença em relação
ao Kinesis, porque o Kinesis tem um limite
rígido de um megabyte para o tamanho da mensagem.
Agora, em um nível mais alto,
você reconhecerá que as arquiteturas de cluster do Kafka
devem ser muito semelhantes às do Kinesis.
Então, agora vamos ver o que acontece em seu cluster.
Portanto, você tem corretores nos corretores do Apache Kafka, e os dados
serão replicados dentro deles.
Portanto, neste
exemplo, mostrei três corretores em seu cluster do Kafka.
Agora, os produtores podem ser seu código,
podem ser o que você quiser.
Você pode criar produtores para obter dados do Kinesis
e colocá-los em clusters do Kafka ou
IoT ou RDS, etc.
Portanto, você só precisa escrever um aplicativo para
pegar alguns dados, colocá-los e enviá-los para o que é chamado de tópico do Kafka.
Agora os tópicos do Kafka são replicados.
Portanto, é assim que seus dados ficam
seguros em várias zonas de disponibilidade.
Assim, depois que ele for gravado em um tópico do Kafka e replicado, os
consumidores, que serão o seu código,
serão extraídos dos tópicos do Kafka.
E então, os consumidores podem fazer o que quiserem.
Eles podem fazer algumas lógicas de processamento
ou enviar os dados para fontes de dados de destino.
Como EMR, S3, SageMaker, Kinesis,
RDS, etc., etc.
Portanto, como você pode
ver, é bastante semelhante ao Kinesis.
A diferença é que as APIs são diferentes,
as ferramentas são diferentes
e o Kafka será muito mais configurável, o que permitirá
que você contorne alguns limites do Kinesis.
Portanto, em termos de configuração, você escolhe
um número de zonas de disponibilidade.
Portanto, recomenda-se três ou dois.
Em seguida, você escolhe a VPC e as sub-redes.
Este é um cluster privado.
Você escolhe o tipo de instância
do broker, por exemplo, no m5 large, EC2 Instance.
O número de corretores por AZ e você pode
adicionar corretores ao longo do tempo.
E isso lhe dá, no final, um
Zookeeper por zona de disponibilidade e um
broker Kafka por AZ.
Portanto, neste exemplo,
ou um, dois por AZ, por exemplo, neste exemplo.
Portanto, temos três nós
do Zookeeper, seis brokers do Kafka e três AZ neste exemplo.
Por fim, você escolhe o tamanho do volume do
EBS entre um gigabyte e 16 terabytes, o que
permite reter os dados pelo tempo que for necessário, com base
nos requisitos de tempo.
Mais uma vez, talvez isso lhe dê um pouco mais de flexibilidade
em relação aos fluxos de dados do Kinesis.
Está bem.
Agora, a segurança é muito importante no Apache Kafka e talvez
você tenha que responder a uma pergunta
sobre ela no exame.
Vejamos o exemplo de um cluster com três corretores.
Portanto, podemos obter criptografia
em voo entre cada corretor usando TLS.
Portanto, por padrão, ele está
ativado, mas você pode desativá-lo, se quiser,
para melhorar o desempenho.
Você também recebe criptografia TLS opcional em trânsito entre
os clientes e o corretor.
E, novamente, por padrão, isso está
ativado, mas você pode desativá-lo
também por motivos de desempenho.
Você obtém criptografia em repouso para o seu volume EBS usando
o KMS, portanto, isso está ativado.
Agora, para a segurança
da rede, você pode anexar grupos de segurança aos seus clientes
Kafka para garantir que a segurança
da rede seja feita entre seus brokers e sua instância EC2.
E o mais importante será a autenticação
e a autorização, o que é muito importante.
Portanto, isso permite que você defina quem
pode ler e quem pode gravar em quais tópicos do cluster do Kafka.
Portanto, há três tipos de mecanismos atualmente
no Apache Kafka.
O primeiro é chamado de TLS mútuo.
Isso significa que os certificados TLS são usados para criptografia,
mas também para autenticação.
Por isso, escrevi
"Mutual TLS (AuthN)" para autenticação.
Nesse caso, ao usar esse mecanismo, é necessário usar
as ACLs do Kafka para acessar a lista de controle para fazer
a autorização no nível do tópico.
E as ACLs do Kafka são um mecanismo em seu cluster do Kafka.
Você também pode usar algo chamado "SASL/SCRAM",
que é, para simplificar, nome de usuário
e senha para autenticação.
E, novamente, você precisaria usar as
ACLs do Kafka para autorização
ou pode usar o IAM Access Control.
E o controle de acesso ao IAM permite que você
faça tanto a autenticação quanto a autorização usando políticas do IAM.
Isso é mais ou menos o que você obtém com o Kinesis Data Streams.
Portanto, isso é algo
que, novamente, você precisa saber ao fazer o exame
de segurança do Kafka.
O que você precisa saber, porém,
é que as ACLs do Kafka para Mutual TLS e SASL/SCRAM não podem ser gerenciadas
usando políticas de IAM.
Eles precisam ser definidos em seu cluster do Kafka.
Ok, então é isso para a segurança.
Em seguida, temos o monitoramento.
Portanto, temos o CloudWatch Metrics e ele tem três níveis.
Temos o monitoramento básico para obter métricas
no nível do cluster e do broker.
Monitoramento aprimorado para obter mais métricas do broker
ou monitoramento em nível de tópico.
Portanto, para cada fluxo de dados em seu cluster,
e isso permite que você obtenha métricas aprimoradas no nível do tópico.
O Prometheus for Open-Source Monitoring,
que permite extrair dados diretamente usando o JMX
Exporter ou o Node Exporter usando o protocolo
Prometheus.
E o Broker Log Delivery pode ser feito para logs
do CloudWatch, Amazon S3 ou Kinesis Data Streams.
Então é isso para a MSK.
Lembre-se apenas de que ele é um substituto para o Kinesis e
mais configurável.
Você precisa se lembrar da segurança do MSK, pois ela
será solicitada no exame.
E nos veremos na próxima palestra para falar sobre o
Kinesis Data Streams versus o Amazon MSK.
