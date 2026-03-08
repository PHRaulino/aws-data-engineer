O Apache Airflow é uma solução popular de gerenciamento de fluxo de trabalho,
e a Amazon também oferece suporte a ele na forma de fluxos
É basicamente um ambiente gerenciado
e hospedado para o Apache Airflow.
O Apache Airflow é uma ferramenta de fluxo de trabalho orientada a lotes
e pode desenvolver, programar e monitorar seus fluxos de trabalho e controlar
o fluxo de seus dados e seu pipeline
de engenharia de dados.
O problema é que você os define usando código Python,
portanto, não será usada uma interface gráfica de usuário
do tipo arrastar e soltar para definir esses fluxos de trabalho.
Na verdade, você precisa escrever código Python para configurá-los.
E o que esse código Python precisa
fazer é criar o que é chamado de gráfico cíclico direcionado ou
A-D-A-G-A DAG, mais ou menos da mesma forma que o Apache Spark
funciona, certo?
O que o Amazon NWAA traz para a mesa é um serviço gerenciado para o fluxo
de ar do Apache.
Portanto, você ainda precisa escrever o código
para ele e descobrir como ele é configurado,
mas não precisa lidar com a manutenção
ou a instalação do serviço em si.
Portanto, é apenas uma maneira de controlar o fluxo de ar com um pouco mais de facilidade.
Portanto, se você tiver um fluxo de trabalho
mais complexo ou precisar fazer algum tipo de coordenação complexa
com ETL ou talvez preparar dados de aprendizado de máquina,
isso pode ser algo que você queira fazer em Python e o Apache
Airflow pode ser uma boa opção para isso.
Aqui está um exemplo muito simples disso.
Então, digamos que, por exemplo, estamos
criando algumas tarefas.
Um deles é chamado Hello, que apenas chama o operador
do Bash para ser executado no console do Bash.
Echo, olá. E temos outra coisa chamada fluxo
de ar, que é apenas uma função que imprime a palavra fluxo de ar.
Em seguida, definimos uma dependência entre essas duas tarefas.
Dizemos Hello, carrot, carrot, airflow, e isso
cria essa dependência no Python.
E depois que fizermos isso, o fluxo de ar não só garantirá que ele
faça o que precisa ser feito no cronograma
que você quiser, mas também poderá criar
uma pequena visualização desse fluxo de trabalho,
que você vê nesse diagrama aqui, você vê na parte inferior que temos
o Hello que aponta para o fluxo de ar como a próxima etapa.
E ao redor dele, você pode ver todas as informações sobre a frequência
com que é executado, qual é a programação, coisas desse tipo.
Portanto, ele tem essa pequena e agradável interface da Web que
pode ser usada para visualizar o que está sendo feito e controlar o agendamento.
Mas os gráficos cíclicos direcionados reais
do que ele realmente faz é algo para o qual você
precisa escrever código Python.
Lembre-se de que o exame nunca pedirá que você
escreva código, portanto, não se preocupe muito com a sintaxe.
Você só precisa entender que cria dags com Python
usando fluxo de ar.
Então, como isso se integra à Amazon?
Portanto, seus gráficos ASIC direcionados, o código Python
que realmente cria esses fluxos de trabalho são carregados no S3 e, em seguida, são
carregados nos fluxos de trabalho gerenciados da Amazon
para o Apache airflow, onde o airflow os utiliza.
Você também pode compactar esse código Python
junto com todos os plug-ins necessários
ou outras dependências que o código possa ter.
Portanto, tudo permanece autônomo no S3.
Assim que o NWA o captar, ele orquestrará e programará tudo
o que você precisa, definido por cada gráfico acíclico
direcionado.
É difícil dizer isso. O MWAA é executado em um VPC.
Você deve implantá-lo em pelo menos
-: Duas zonas de disponibilidade para fins de redundância.
Você também pode conectá-lo a pontos
de extremidade públicos e privados que são gerenciados via IAM,
e isso controlará o acesso ao servidor
da Web do airflow.
Lembre-se da cena que vimos no slide anterior, em
que você tem aquela pequena e
agradável interface do usuário para
visualizar esses fluxos de trabalho e agendá-los; se quiser acessar isso
fora da sua VPC, precisará de um endpoint público para fazer isso.
Ele é dimensionado automaticamente.
Portanto, sob o capô, há operadores de fluxo de
ar fazendo tudo isso acontecer.
O bom do MWAA é que ele os dimensiona automaticamente,
até os limites que você possa definir para
controlar os custos, integrando-os
a outros serviços.
Portanto, o MWAA depende apenas de integrações de código aberto com
outros serviços da Amazon, mas
há muitos deles por aí.
Assim, você pode vincular o MWAA ao Athena e ao AWS Batch. CloudWatch.
DynamoDB Datas Sync, EMR, fargate EKS, Kinesis Glue, Lambda,
Redshift, S-Q-S-S-N-S, SageMaker S3 e muito mais.
E, obviamente, todos os serviços de segurança de que você pode precisar
para acessar esses serviços.
Como o AWS Secrets Manager, os agendadores e os próprios trabalhadores
são implementados nos contêineres do AWS Fargate.
E aqui está uma pequena olhada rápida
na arquitetura subjacente.
Basicamente, há dois VPCs sob o capô com o MWAA.
Há um VPC de cliente que contém todos os agendadores
e workers, e eles estão se comunicando com os serviços com os
quais você está trabalhando a partir desses DAGs.
Assim, ele pode sair e se
comunicar com o CloudWatch, S3 SQS, o que você precisar.
E, por meio de endpoints de VPC, ele também se comunica com
um banco de dados de metadados, restaurando esses fluxos de trabalho,
e também com o servidor da Web de fluxo de ar, que
é a interface do usuário para visualizar e agendar
esses fluxos de trabalho.
Portanto, mais uma vez, se você não tiver uma interface de rede
pública, não há como acessar esse servidor da Web de fora,
mas se você estiver dentro dessa VPC de serviço, ainda poderá
acessá-lo de lá.
