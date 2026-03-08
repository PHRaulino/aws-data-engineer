Na verdade, eles se esforçaram muito
para integrar o EMR ao ecossistema da AWS em vários pontos.
Então, vamos falar sobre elas,
pois é importante conhecê-las.
Portanto, ele usa o Amazon EC2 como base
para as instâncias que compõem os
nós do cluster EMR.
Portanto, sob o capô, você tem instâncias do EC2
que estão executando os nós nesse cluster para você,
e elas podem fazer tudo o que o EC2 pode fazer.
Ele também usa o Amazon VPCs para configurar
a rede virtual na qual você está
lançando suas instâncias.
Portanto, você está lançando
as instâncias para esse cluster em um Amazon VPC.
Ele se integra ao Amazon S3.
Portanto, normalmente no Hadoop você só tem
acesso ao sistema de arquivos distribuídos do Hadoop,
o HDFS, mas eles ampliaram isso
com o EMR para que você possa realmente armazenar
seus dados de entrada e saída no Amazon S3.
E falaremos mais sobre como isso funciona.
Além disso, ele se integra ao Amazon CloudWatch,
como praticamente tudo, para
monitorar o desempenho do seu cluster e configurar
quaisquer alarmes que você possa
precisar configurar para o cluster.
Você pode usar o AWS IAM para configurar permissões no EMR e, em
breve, falaremos mais sobre segurança.
O CloudTrail pode ser usado para auditar
as solicitações feitas ao serviço EMR
e o pipeline de dados do AWS se integra ao EMR para que você
possa programar e iniciar
seus clusters como parte de um pipeline de dados.
Lembre-se de que você pode configurar esses clusters
transitórios que iniciarão automaticamente as etapas
e, com um pipeline de dados, você
pode programar quando isso ocorrerá
como parte de um processo maior.
Então, vamos falar mais sobre o armazenamento com o EMR.
Portanto, há várias opções disponíveis para você.
Um deles é o HDFS.
Portanto, lembre-se de que esse é fundamentalmente
um cluster do Hadoop em execução no EC2.
E se quiser usar o sistema de arquivos HDFS, você pode.
Portanto, isso usará o armazenamento local em cada
instância para distribuir o armazenamento em todo o cluster.
A forma como o HDFS funciona é armazenando várias
cópias de cada bloco de arquivo nas instâncias
do cluster.
Dessa forma, temos redundância, caso um nó fique inoperante,
ele pode se recuperar, pois
sempre garante que seus
dados sejam copiados para mais de um local.
Dessa forma, se uma instância individual falhar, nenhum
dado será perdido, ela poderá
simplesmente seguir em
frente e redirecionar as coisas para a outra cópia de backup e começar
a criar uma nova cópia de backup.
Portanto, cada arquivo no HDFS é armazenado como
blocos, e esses blocos são o que é distribuído pelo cluster.
Não se trata de arquivos, mas de blocos de dados que compõem cada arquivo.
Agora, por padrão, o tamanho
de um bloco no HDFS é de 128 megabytes, o que pode
ser importante.
No entanto, o problema é que, com o EMR,
esse armazenamento HDFS será efêmero.
Assim que você desligar o cluster, perderá
todo esse armazenamento.
Esse é o tipo de problema com o EMR.
Não é necessariamente algo que você deixe
em execução para sempre,
como faria com um cluster tradicional do Hadoop, embora
seja possível.
Mas, como você está sendo cobrado por minuto,
é preciso lembrar que,
assim que encerrar esse cluster,
se tiver a ideia de economizar dinheiro
e parar de acumular sua conta,
que pode aumentar rapidamente com um cluster grande, esses
dados desaparecerão.
E isso é um problema, certo?
Portanto, se você estiver gravando toda a sua saída no HDFS e desligar
o cluster porque alguém queria economizar
alguns dólares, todos esses dados desaparecerão e você terá um
dia muito ruim.
No entanto, você ainda pode usá-lo para armazenar
em cache resultados intermediários ou cargas
de trabalho que tenham E/S aleatória significativa.
O bom do HDFS é que o Hadoop tentará processar
os dados onde eles estiverem armazenados no HDFS.
Portanto, ele tentará distribuir
o processamento de seus dados
de forma que o processamento de um
bloco ocorra no mesmo nó em que esse
bloco está armazenado.
Essa é uma otimização muito importante que o HDFS permite, mas é realmente um problema
que atrapalha o desempenho, pois assim que você
encerra o cluster, tudo desaparece.
Então, o que você faz?
Bem, é aí que entra o EMRFS e a
ideia do EMRFS, ou sistema de arquivos
EMR, é acessar o S3 como se fosse o HDFS.
Portanto, com o EMRFS,
você pode gravar dados como se fosse o HDFS.
Basta usar um prefixo diferente
para o local onde você está gravando, como o S3,
e isso permite o armazenamento persistente
mesmo após o término do cluster.
Agora, um problema que costumava ser um problema
era a questão da consistência.
Então, o que acontece se você tiver vários
nós gravando no mesmo local no S3 ao mesmo tempo.
Pode haver um problema de contenção,
como quem realmente recebe...
Quem vai primeiro.
Portanto, costumava haver
uma coisa chamada visão consistente do EMFRS
e, a essa altura, não
tenho certeza se o exame reflete que isso
não é mais necessário.
Portanto, talvez você ainda precise saber sobre isso.
Às vezes, o exame atrasa em vários meses
as mudanças na tecnologia.
Portanto, ainda vou mencioná-la aqui,
mas é uma opção para a consistência do S3, em
que ele usa o DynamoDB para rastrear a consistência
do acesso ao arquivo para esse armazenamento de dados
subjacente do S3, para garantir que, se
você tiver vários nós do cluster do
EMR acessando o mesmo arquivo e o S3 ao mesmo tempo,
ele ainda funcionará.
E isso pode ser muito complicado, pois, se houver
muito tráfego de E/S, talvez seja necessário ajustar a capacidade
de leitura correta na instância subjacente
do Dynamo DB para que ele funcione de forma
confiável, o que é um pouco trabalhoso.
Felizmente, a Amazon percebeu que isso era um problema
e, em 2021, o próprio S3 passou
a ser fortemente consistente.
Portanto, agora que o S3 garante a consistência, não precisamos
mais nos preocupar com a exibição consistente do EMRFS.
Portanto, isso não é mais um problema.
Agora ele funciona magicamente.
Agora, ainda estamos abrindo mão da otimização do processamento de dados na
mesma máquina em que eles estão armazenados.
Obviamente, o S3 armazenará esses
dados em outro lugar da rede.
Portanto, em teoria, não é tão rápido quanto usar o HDFS, mas,
na prática, ainda é bastante rápido.
O S3 pode ser bastante rápido e tudo
está no mesmo data center.
Portanto, na prática, você ainda pode criar aplicativos
eficientes em grande escala usando o EMFRS que usa o
S3 em vez do sistema de arquivos HDFS incorporado
ao Hadoop.
Isso permite que você execute aplicativos do Hadoop usando
o S3 como um armazenamento de dados persistente
para que, quando você encerrar o cluster,
seus dados não desapareçam.
Outras opções são usar o sistema de arquivos local.
Obviamente, isso também será efêmero
e não terá backup em nenhum lugar.
Portanto, embora seja rápido, não há
muito disso e é adequado
apenas para dados temporários.
Portanto, se você quiser ter buffers ou caches temporários,
tudo bem, você pode gravá-los
localmente, mas certifique-se de que não está dependendo
da permanência deles por muito tempo.
Além disso, com o armazenamento de blocos elástico para
HDFS, você pode usar o EMR somente em tipos de EBS
como M4 ou C4 usando esse recurso.
Mas, novamente, assim como o armazenamento
local, o armazenamento de blocos elásticos também será excluído
quando o cluster for encerrado.
Portanto, não há muito mais a oferecer além do HDFS, mas se você não tiver
um sistema de arquivos local porque está usando um
tipo de instância somente EBS, ele ainda
poderá usar o EBS para esse armazenamento
local e para fazer o backup do HDFS.
Agora, os volumes EBS só podem ser anexados quando você
estiver iniciando um cluster no número dois.
Portanto, você não poderá expandir essa capacidade
de armazenamento depois, o que é outro motivo para evitá-lo.
Lembre-se também de
que, se você desconectar manualmente um volume EBS enquanto
ele estiver em execução, o EMR tratará isso como uma falha e o
substituirá automaticamente.
Portanto, ele é resistente a esse modo de falha, pelo menos.
Mas, novamente, se você quiser um armazenamento
persistente que dure depois que o cluster for encerrado,
terá que usar o EMFRS com o S3 para isso.
