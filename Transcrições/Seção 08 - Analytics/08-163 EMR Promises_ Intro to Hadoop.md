Então, vamos falar sobre
Antes de mais nada, vamos falar um pouco sobre preços.
Portanto, o EMR cobra por hora.
Portanto, quanto mais tempo você deixar seu cluster em execução,
mais eles cobrarão.
E isso pode aumentar muito rapidamente
se você estiver usando tipos de instância
caros, como instâncias de GPU e coisas do gênero.
Portanto, tenha isso em mente.
Se você puder executar sua tarefa como um conjunto de etapas que iniciam
e param automaticamente o cluster quando ele é
concluído, você economizará muito dinheiro dessa forma.
No entanto, se você precisar deixar seu cluster em execução 24 horas por
dia, 7 dias por semana, isso pode ficar caro e você precisa estar atento a isso.
No que diz respeito a falhas, se um nó central falhar,
o EMR provisionará automaticamente um novo
nó para você.
Portanto, você não precisa se preocupar com isso, pelo menos.
E isso fará com que as coisas continuem automaticamente
de onde pararam.
Se você precisar redimensionar
as coisas, se precisar adicionar capacidade,
provavelmente a melhor maneira
de fazer isso é adicionar ou remover nós de tarefas em tempo real.
Lembre-se de que os nós de tarefa são como
os nós principais, mas não
têm capacidade de armazenamento própria.
Não há capacidade de HDFS associada a um nó de tarefa.
Normalmente, você não se importa
com isso, pois provavelmente está usando o EMRFS
para se comunicar com o S3 para que
seus dados sejam mais persistentes, certo?
Mas, mesmo que esteja usando o HDFS, você ainda pode usar nós
de tarefas para aumentar a
capacidade de processamento se não
precisar aumentar a capacidade de armazenamento
ao mesmo tempo.
Um bom exemplo disso é, digamos,
que você esteja administrando um site de comércio eletrônico,
como o da Amazon ou algo assim, e precise
ter esse grande aumento de dados associado à época do Natal
ou algo parecido.
Vamos supor que seu armazenamento seja bom, mas que
você precise processar muito mais esses dados.
Há muito mais tempo de CPU envolvido nesse processamento.
Você pode simplesmente adicionar temporariamente vários
nós de tarefas ao cluster de EMR para lidar com esse aumento no processamento
e, posteriormente, remover esses nós de tarefas quando
o aumento tiver passado.
Portanto, adicionar e remover nós de tarefas em tempo
real é uma boa maneira de lidar com picos temporários
nas necessidades de CPU de processamento.
Lembre-se disso.
Você também pode redimensionar os nós principais de um
cluster em execução sem muitos
problemas, e isso pode ser uma forma de
aumentar a capacidade de processamento e do HDFS.
Portanto, se você precisar aumentar
o tempo de processamento e a capacidade de armazenamento, e não
estiver usando algo como o EMRFS, em que
o armazenamento está em outro lugar, poderá
redimensionar os nós principais também.
Também é possível adicionar e remover um nó central em tempo real.
Isso é algo novo.
Mas, você sabe, nem sempre é uma boa ideia.
Se você remover um nó central, lembre-se
de que também estará removendo o armazenamento subjacente.
Portanto, se você estiver usando a capacidade do HDFS,
estará arriscando a perda de dados
ao remover um nó central em tempo real.
Portanto, só porque você pode fazer isso, não significa que deva.
Novamente, apenas para recapitular, de modo
geral, se você precisar de um aumento temporário na capacidade de processamento, adicionar
nós de tarefa é uma boa maneira de fazer isso.
Se você precisar adicionar capacidade de armazenamento também no HDFS,
poderá redimensionar um nó central.
Também é possível adicionar e remover nós de núcleo em tempo
real, assim como é possível com os nós de
tarefa, mas há um pouco mais de risco de perda de dados se você
estiver fazendo isso nos nós de núcleo em vez de nos nós de tarefa.
Então, vamos falar um pouco
mais sobre como o dimensionamento gerenciado funciona especificamente no EMR.
Portanto, o dimensionamento gerenciado foi introduzido em 2020.
Antes disso, eles o chamavam de escalonamento automático de EMR.
Essa era a maneira antiga de fazer isso.
E criou regras de dimensionamento personalizadas
com base nas métricas do CloudWatch.
Portanto, antes de 2020, ou mesmo
na primeira metade de 2020, era assim que funcionava
o escalonamento automático no EMR.
Você monitorava automaticamente as métricas do CloudWatch
e podia adicionar ou remover automaticamente a capacidade
do seu cluster EMR, mas isso era limitado
apenas a grupos de instâncias, portanto, não era possível
misturar e combinar diferentes
tipos de instâncias com o dimensionamento automático.
Isso mudou em 2020 com o dimensionamento gerenciado por EMR.
Portanto, agora, além de oferecer suporte a grupos de instâncias,
ele também pode oferecer suporte a frotas de instâncias.
Portanto, ele pode aumentar e diminuir
seu spot, seu on-demand e suas instâncias regulares em um Savings Plan
dentro do mesmo cluster.
E isso está de fato disponível para cargas
de trabalho Spark, Hive ou YARN especificamente no EMR.
Portanto, quando você está aumentando o dimensionamento no dimensionamento
gerenciado do EMR, a maneira como ele
funciona é que, primeiro, tentará adicionar
nós de núcleo e, depois, se atingir o limite,
adicionará nós de tarefa.
E isso será feito até o número máximo de unidades
que você especificar.
Então, a configuração que você fornece no dimensionamento gerenciado
é: qual é o número máximo de nós de núcleo que quero adicionar?
Qual é o número máximo de notas de tarefas que desejo adicionar?
Se for necessário reduzir a escala,
se ele vir algum tipo de métrica do CloudWatch
que sugira que você tem capacidade demais, ele começará removendo
os nós de tarefa e, em seguida, removendo
os nós de núcleo.
Novamente, não mais do que as restrições mínimas que você definiu.
Portanto, você pode dizer que não quero menos do que esse número de nós de tarefa.
Não quero menos do que essa quantidade de nós principais.
E o dimensionamento gerenciado honrará
isso à medida que for necessário reduzir o dimensionamento.
Além disso, observe que os nós pontuais sempre serão removidos
antes das instâncias sob demanda com escalonamento gerenciado, certo?
Portanto, esse é o dimensionamento gerenciado e como ele funciona.
Basicamente, você especifica um número máximo
de unidades e uma restrição mínima no número de nós, os
nós principais e os nós de tarefas são gerenciados,
e você pode aplicar isso em uma frota e
não apenas em um grupo de instâncias.
Então, vamos começar a falar mais sobre os aplicativos
que você executará em seu cluster de EMR.
Portanto, fundamentalmente, é um cluster do Hadoop.
Então, vamos falar sobre o Hadoop com um pouco mais de profundidade.
O que é o Hadoop?
Bem, a arquitetura do Hadoop é composta por vários módulos.
Esses módulos aqui.
Eles compõem o que chamamos de Hadoop comum ou núcleo do Hadoop.
Essa é uma espécie de base do próprio Hadoop, esses
três componentes que você vê aqui.
Essas são as bibliotecas e os utilitários necessários
para que outros módulos do Hadoop sejam desenvolvidos com base nelas.
Ele fornece todas as abstrações
do sistema de arquivos e do sistema operacional
de que precisamos no topo do seu cluster
e os arquivos JAR e scripts necessários para
iniciar o próprio Hadoop.
Portanto, na parte inferior,
temos o sistema de arquivos distribuídos do Hadoop, o HDFS.
Esse é um sistema de arquivos distribuído e dimensionável
que armazena blocos de dados em instâncias do cluster.
Ele armazena, novamente, várias cópias desses blocos
em instâncias diferentes para garantir que nenhum dado seja perdido
se uma instância individual falhar.
Agora, no EMR, esse é um armazenamento efêmero.
Seus dados no HDFS serão perdidos após o encerramento do cluster.
Mas ainda é útil para armazenar em cache resultados intermediários
durante o processamento do MapReduce ou para
cargas de trabalho com E/S aleatória significativa.
Ou se você pretende deixar seu cluster de EMR em execução para sempre,
tudo bem, vá em frente.
Você pode usar isso para armazenamento
persistente, mas não será barato.
Sobreposto ao YARN do HDFS, que significa
mais um negociador de recursos e é basicamente
um nível de abstração que foi adicionado
ao Hadoop 2. 0 entre o MapReduce e o HDFS.
E, como veremos, isso nos permite executar
substituições do MapReduce que são melhores em cima do HDFS.
Basicamente, ele permite que você
gerencie centralmente os recursos do cluster para que possamos
ter mais de uma estrutura de processamento de dados.
E não estamos vinculados diretamente ao MapReduce,
o que costumava ser o caso no Hadoop 1.
Agora, a estrutura central de processamento de dados que faz
parte do próprio Hadoop é o MapReduce.
Ele ainda está lá fora hoje.
É uma estrutura de software para escrever facilmente aplicativos
que processam grandes quantidades de dados em paralelo
em grandes clusters de hardware de commodity de maneira confiável
e tolerante a falhas.
Você provavelmente pode dizer que essa é a definição oficial, certo?
Mas, basicamente, por que ele é chamado de MapReduce?
Bem, ele é composto por mapeadores e redutores.
Portanto, uma função de mapa no MapReduce mapeará os dados para
conjuntos de pares de valores-chave.
E esses são basicamente os resultados intermediários
do seu processamento.
Portanto, trata-se basicamente de analisar
seus dados, extrair os dados que você precisa processar
e organizá-los como pares de valores-chave.
Em seguida, as funções redutoras combinam esses resultados intermediários, aplicam
algoritmos adicionais a eles e produzem
o resultado final.
Portanto, em geral, você tem mapeadores e redutores
que extraem os dados, reduzem-nos à resposta
final que você deseja e os
enviam para algum lugar.
Originalmente, era assim que se fazia o processamento distribuído de arquivos
em um cluster do Hadoop, mas atualmente ele
foi amplamente suplantado pelo Apache
Spark, porque é muito mais rápido, muito mais extensível e pode fazer mais
coisas.
Em seguida, falaremos sobre o Spark.
