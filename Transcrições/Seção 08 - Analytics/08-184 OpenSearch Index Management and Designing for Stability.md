foi adicionando diferentes tipos de armazenamento
para armazenamento frio, morno e quente.
Vamos falar um pouco sobre isso,
pois você pode ser questionado a respeito.
Portanto, seus nós de dados padrão
usam o que é chamado de hot storage por padrão,
e esse é o armazenamento em seus nós de dados que está ali mesmo
no nó, seja por meio
de um armazenamento instantâneo
ou por meio de um volume EBS (elastic block store).
Isso lhe proporcionará o desempenho mais rápido.
É como o armazenamento normal em uma instância do EC2,
portanto, é o padrão que você espera obter.
Mas também é o mais caro, portanto, como alternativa, eles ofereceram algo novo
chamado armazenamento UltraWarm e armazenamento UltraWarm,
que eles também chamam de warm
na documentação de forma praticamente intercambiável,
que usa o S3 para realmente fazer
o backup dos dados, além de uma camada de cache para torná-lo,
bem, mais quente do que warm e talvez UltraWarm, eu acho, é o que eles estão chamando
lá.
O armazenamento UltraWarm é melhor para índices
que não recebem muitos direitos.
Portanto, para coisas que são imutáveis, como dados de registro, o armazenamento
UltraWarm pode ser uma boa opção para isso.
O desempenho é mais lento, mas o custo é muito menor
porque você está usando o S3 em vez de um armazenamento local.
Agora, para usar o armazenamento UltraWarm,
é necessário ter um nó mestre dedicado e, na prática,
você geralmente tem três deles, mas falaremos
mais sobre isso daqui a pouco.
Não é possível ter um cluster autônomo sem um
nó mestre se você quiser usar diferentes
tipos de armazenamento.
E se você quiser economizar ainda mais dinheiro,
agora também há armazenamento a frio disponível.
Ele também usa o S3 para fazer o backup e é ainda mais barato.
Destina-se a usos como pesquisa periódica
ou análise forense de dados antigos.
Por exemplo, se você tiver dados de registro muito
antigos com os quais não se importa mais,
o armazenamento a frio pode ser um bom lugar para eles.
Novamente, você deve ter um mestre
dedicado e também deve ter o UltraWarm ativado
para usar o armazenamento a frio.
Um problema com o armazenamento a frio é que
atualmente ele não é compatível com os tipos de instância
T2 ou T3 nos nós de dados.
E se você estiver usando o controle de acesso refinado, precisará
mapear os usuários para a função de gerente frio nos painéis do
opensearch para usá-lo corretamente, portanto,
há alguns detalhes de implementação.
E você também pode migrar seus dados entre
diferentes tipos de armazenamento conforme desejar
e, como veremos, há maneiras de automatizar a migração
de dados do armazenamento quente para o quente e para o frio ao longo do tempo, se
desejar.
Assim, você não precisa decidir antecipadamente que
tipo de armazenamento deseja para seus dados.
Na verdade, você pode mover dados em seus índices
para frente e para trás entre eles, conforme necessário.
E isso nos leva ao Index State Management, na
verdade mais um recurso do Elasticsearch
em geral, e poderíamos falar por horas e horas
sobre os detalhes e as profundezas do próprio Elasticsearch.
Há um curso completo sobre isso que dura uma eternidade,
mas vamos falar apenas o suficiente
para você passar no exame.
Portanto, a ideia do Index State Management, ou ISM, é automatizar
as políticas de gerenciamento de índices,
e quais são alguns exemplos disso?
Por exemplo, se você tiver índices antigos que
deseja excluir após um período de tempo,
talvez tenha índices divididos
por mês ou algo assim e só se preocupe com os dados
dos últimos três anos, poderá ter uma
política de gerenciamento de estado do índice que exclua
automaticamente esses índices antigos após
um determinado período de tempo.
Você também pode usá-lo para mover
os índices para um estado somente leitura após algum período de tempo.
Talvez seja necessário fazer isso por motivos
de conformidade para garantir que você não esteja mexendo nos dados após o fato.
E, como falamos no slide anterior, você também
pode usar isso para mover automaticamente os índices
do armazenamento quente para o UltraWarm e para o armazenamento frio ao longo do tempo.
Portanto, se você sabe que acessará
seus dados com menos frequência, quanto mais antigos eles se tornarem, talvez faça
sentido movê-los automaticamente para um
armazenamento cada vez mais frio com o passar do tempo, a fim de economizar
algum dinheiro.
Você também pode usar o Index State Management
para reduzir sua conta de réplica ao longo do tempo.
Portanto, se você tiver um índice que, à medida que o
tempo passa, se preocupa menos com ele, também
poderá reduzir a contagem de réplicas ao longo
do tempo se não se importar tanto com a perda desses dados ao longo do tempo.
E você também pode usá-lo para automatizar instantâneos
de índices, apenas para fazer o backup do índice e colocá-lo em algum lugar.
As políticas de ISM são executadas a cada 30 a 48 minutos.
Esse é um número estranho, não é?
A razão pela qual ele tem esse intervalo
é porque há um jitter aleatório introduzido nele
para garantir que você não esteja executando o estado do índice em todos
os seus índices ao mesmo tempo.
Isso pode acabar afetando o desempenho de seu cluster.
Além disso, você pode configurar o Index State Management
para enviar notificações assim que elas forem concluídas.
E uma coisa que é específica da Amazon é que você pode
até mesmo enviar uma notificação
por meio do Amazon Chime para uma sala, para
que ela saiba que uma política foi adotada.
Mais informações sobre gerenciamento de índices.
Enrolamentos de índice.
Portanto, você também pode acumular periodicamente seus dados
antigos em índices resumidos.
Assim, você pode economizar muito dinheiro em custos de armazenamento.
Se, após um determinado período de tempo,
você não precisar de informações detalhadas,
mas apenas das informações resumidas, essa é uma
ótima ideia para economizar dinheiro.
Portanto, esse novo índice acumulado pode ter menos campos.
Talvez você esteja descartando alguns
campos que não lhe interessam
após um determinado período de tempo.
Ou coercer baldes de tempo, essa
é outra maneira de consolidar as coisas.
Além disso, as transformações de índice estão disponíveis,
com a mesma ideia dos roll-ups,
mas o objetivo aqui não é resumir os dados, mas apenas analisá-los de forma
diferente para criar uma visão diferente
deles.
E você pode fazer coisas como agrupamentos
e agregações lá.
Assim, por exemplo, eu poderia agrupar todos os meus
dados por algum identificador e ter uma exibição
separada que fosse agrupada por esse campo separado que me interessa.
Ou posso ter agregações, talvez
eu me preocupe com a soma de tudo dentro desse grupo
ou com a soma de tudo em um determinado período de
tempo, ou com a média, o que quer que seja.
Uma transformação de índice pode criar automaticamente essas novas
visualizações para você.
Vamos falar também sobre a replicação entre clusters
no contexto do gerenciamento de índices.
Assim, você pode replicar seus índices,
mapeamentos e metadados em diferentes domínios, e isso
é importante por alguns motivos.
Em primeiro lugar, ele garante alta disponibilidade
no caso de uma interrupção.
Portanto, se você estiver replicando todos os seus
dados para outro cluster que esteja em outro data
center em algum lugar, ou talvez
até mesmo em uma região diferente, se essa região
ou esse data center ficar inoperante, você ainda terá
essa cópia de backup em execução em outro lugar, porque
você a estava replicando.
Além disso, é uma ideia reduzir a latência
se você tiver um aplicativo global.
Portanto, você pode replicar seus dados geograficamente
em todo o mundo usando a replicação para melhorar
a latência de diferentes locais em todo o mundo.
Portanto, se alguém estiver tentando
atingir seu cluster opensearch da Europa, é melhor ter
uma réplica desse cluster na Europa do que fazê-lo
atravessar o oceano para atingir um cluster localizado
nos Estados Unidos ou algo assim.
O modo como funciona é que você configura
o que é chamado de índice de seguidores,
que extrai dados do que eles chamam de índice de líderes.
Portanto, o índice líder é basicamente sua cópia principal
e o seguidor será o replicante, apenas a terminologia
que eles usam lá.
E para usar a replicação entre clusters, é necessário
ter o controle de acesso refinado ativado
no cluster opensearch e a criptografia
nó a nó para garantir que possamos fazer isso com segurança.
Há também um recurso semelhante chamado Remote Reindex, que
permite copiar índices especificamente
de um cluster para outro sob demanda.
Portanto, se você não precisar replicar todo o cluster
com todos os seus mapeamentos e metadados, o Remote
Reindex permite que você copie apenas um índice
de um cluster para outro sempre que necessário.
Algumas observações sobre a estabilidade do opensearch
que talvez você precise conhecer.
Portanto, antes de mais nada, é importante
ter pelo menos três nós mestres dedicados.
Essa é a melhor prática.
Se você tiver um, ele pode falhar
e você ficará fora de serviço, certo?
Você não pode ter apenas um único nó mestre,
pois esse é um ponto único de falha.
Por que não ter apenas dois?
Bem, o problema com dois nós mestres
é que você pode entrar no
que chamamos de condição de cérebro dividido,
e pode haver um modo de falha
em que você tem dois nós mestres ao mesmo tempo, basicamente,
e ninguém sabe qual deles
é o nó mestre autoritativo de fato.
Portanto, ao ter três nós mestres,
o terceiro decide quem
é o mestre de fato nesse caso.
Portanto, ao ter pelo menos três nós mestres,
você pode evitar o modo de falha de cérebro dividido
e pode evitar o ponto único de falha
de ter apenas um.
Portanto, essa é considerada a melhor prática.
Além disso, certifique-se de não ficar sem espaço em disco.
Na verdade, esse é o problema número um
do opensearch e dos clusters do Elasticsearch em geral.
Portanto, é preciso fazer as contas, certificar-se de que está alocando
capacidade de armazenamento suficiente para o que deseja armazenar.
E eu não ouvi nenhum relato de que o exame tenha entrado nesse
nível de detalhe, mas esse é o
tipo de coisa que eles gostam de perguntar.
Portanto, se você precisar estimar os requisitos de armazenamento
para um determinado conjunto de dados, uma maneira
de chegar a um valor aproximado é considerar o tamanho
dos próprios dados de origem que você
está tentando armazenar vezes 1 mais
o número de réplicas.
Portanto, obviamente, você precisa levar em conta todos
os dados armazenados no cluster primário,
além de todas as réplicas para as quais você possa estar replicando-os
para fins de backup ou de latência, como
falamos, vezes 1. 45, e isso é apenas uma estimativa
de toda a sobrecarga associada ao armazenamento
desses dados.
Além disso, você precisa escolher o número correto de fragmentos.
Isso também é um pouco científico
e, infelizmente, é algo que você precisa experimentar
para obter o equilíbrio certo.
Mas eles também oferecem uma equação aqui que, pelo
menos, lhe dá uma ideia.
Portanto, a ideia aqui é considerar o tamanho dos dados de origem mais
a margem de crescimento que você deseja incorporar
a eles, quanto eu quero supor que quero ter capacidade
excedente para o crescimento desses dados ao longo do tempo, vezes
1 mais a sobrecarga de indexação.
Então, o que é a sobrecarga de indexação?
Bem, ele não está apenas armazenando seus dados; também está
armazenando dados sobre o que é necessário para
indexar esses dados, e isso ocupa espaço adicional.
Normalmente, isso representa cerca de 10%
a mais, portanto, você pode usar isso como uma estimativa.
No entanto, você pode consultar seus índices
para obter o número exato.
Há alguns comandos que você pode enviar para dizer:
"Dê-me o tamanho exato deste índice", e você
pode pegar esses dados, compará-los
com o tamanho dos próprios dados e descobrir
a sobrecarga real de indexação para seu índice específico,
se necessário.
Mas 10% é um bom palpite.
Em seguida, divida esse valor pelo tamanho do fragmento
desejado, pela quantidade de dados que você está colocando
em cada fragmento, e isso deve
lhe dar uma estimativa do número total de fragmentos necessários para armazenar seus dados.
Em alguns casos raros, talvez você também precise
limitar o número de fragmentos por nó.
Entretanto, na prática, isso geralmente não se torna um problema.
Normalmente, você fica sem espaço em
disco antes de ficar sem fragmentos por nó.
Além disso, você precisa escolher seus tipos de instância com sabedoria.
Novamente, você precisa de pelo menos três nós
de dados pelos mesmos motivos.
Um deles é um ponto único de falha e o segundo
é que você pode entrar em estados estranhos.
Pelo menos três é a melhor prática.
E, principalmente, você só precisa pensar nos seus
requisitos de armazenamento.
Mais uma vez, o opensearch é muito pesado em termos de armazenamento,
portanto, você deve pensar principalmente em como
obter os nós certos com armazenamento suficiente.
Alguns exemplos seriam o m6g. grande. pesquisa, todos
eles são . ou, se você precisar
de algo maior, i3. 4xgrande. e se você estiver realmente
armazenando petabytes de informações, poderá
optar por usar o i3. 16xlarge. tipo de instância de pesquisa.
