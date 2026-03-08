falar sobre o EMR ou Elastic MapReduce,
outro serviço muito importante
no mundo da análise de dados na AWS.
O que é EMR?
Novamente, significa Elastic MapReduce.
E o que ele realmente é é uma estrutura
gerenciada do Hadoop que é executada em instâncias do EC2.
Então, basicamente, a Amazon pegou
o Hadoop e o integrou ao EC2.
Isso significa que você pode iniciar um cluster
que executa o Hadoop usando o console do AWS.
Essa é uma estrutura gerenciada, mas
é preciso especificar com quais servidores
você deseja executá-la.
Quantas instâncias você deseja ter em seu cluster.
Qual software você deseja instalar nele.
E, em troca, você poderá realmente
fazer login nessas instâncias
e fazer coisas de baixo nível com elas.
Assim, por exemplo, você
pode dizer que deseja instalar
o Apache Spark em seu cluster EMR.
Portanto, em vez de ter esse sistema totalmente
opaco, como no caso do glue ETL,
em que você não vê os servidores,
se quiser se aprofundar
no assunto e realmente ter acesso
de baixo nível ao Apache Spark e quiser ter controle
explícito sobre os recursos que ele tem, o EMR pode ser para
você.
Você também pode incluir aplicativos como HBase, Presto,
Flink, Hive e outros, sobre os quais falaremos
mais detalhadamente em breve.
Se você quiser desenvolver um código que aproveite
o cluster no EMR, ele oferece
algo chamado EMR Notebooks, onde você pode desenvolver e iterar
seus scripts no cluster, usando apenas um ambiente
de notebook no navegador.
E eles integraram o EMR ou integraram
o Hadoop com a AWS em vários pontos
importantes, sobre os quais também falaremos
mais.
Então, o que compõe um cluster de EMR?
Bem, um cluster EMR é basicamente apenas
um conjunto de instâncias EC2 que estão
executando o Hadoop.
Agora, cada uma dessas instâncias
é chamada de nó.
Cada nó tem uma função dentro do cluster,
que chamamos de tipo de nó.
Portanto, há três tipos diferentes de nós que
uma instância em um cluster EMR pode
estar executando.
Um deles é o nó mestre.
Você sempre precisa de pelo menos um desses.
Portanto, o nó mestre gerenciará o cluster executando
componentes de software
para coordenar a distribuição de dados.
E as tarefas entre outros nós
para processamento.
Sua função é rastrear o status dessas tarefas e monitorar
a integridade de todo o cluster.
Portanto, cada cluster terá um nó mestre.
Você pode até criar um cluster de nó único
que não tenha nada além de um nó mestre.
Portanto, um cluster de EMR de nó único mínimo
teria apenas um nó
mestre que faz tudo.
Às vezes, o nó mestre
também é chamado de nó líder.
Em seguida, temos o nó Core.
Portanto, o nó Core tem componentes de software
que executam tarefas e armazenam dados no
sistema de arquivos distribuídos
do Hadoop, o HDFS, em seu cluster.
Ou, no EMR, pode ser o EMRFS, que
permite que você grave dados no S3.
Mas são os nós principais que
estão fazendo o trabalho real e distribuindo
esse trabalho pelo cluster.
Portanto, o truque aqui é que
seu trabalho seria dividido
em vários nós do Core, cada um deles
responsável por armazenar
uma parte dos dados e por executar
o processamento em uma parte desses
dados.
Portanto, um cluster com vários
nós terá pelo menos um nó Core.
Se você for distribuir seu processamento, precisará
de pelo menos um nó Core.
Agora, o terceiro tipo de EMR é um nó de tarefa.
Portanto, isso é algo novo.
Portanto, um nó de tarefa tem componentes
de software que executam
apenas tarefas, mas não armazenam dados no HDFS ou no EMRFS.
Eles são opcionais.
Portanto, se você precisa adicionar mais capacidade
de processamento ao cluster,
mas não precisa de mais capacidade de armazenamento, um nó
de tarefa pode ser uma boa opção.
E, se você pensar bem, o R costuma usar o S3 para o armazenamento
sob o capô, certo?
Portanto, nem sempre é necessário
ter mais armazenamento disponível em um cluster de EMR, pois tudo
é canalizado para o S3 de qualquer maneira.
Portanto, um nó de tarefa pode fazer muito sentido no EMR quando
você não precisa necessariamente
de uma tonelada de armazenamento no próprio cluster do EMR.
Assim, você economiza dinheiro, certo?
Por exemplo, você não está
pagando por todo o armazenamento que não está usando.
Outra coisa também é que não há risco de perda de dados quando você remove
um nó de tarefa porque ele não pode gravar
dados, certo?
Portanto, você não precisa se preocupar com isso.
Isso significa que é
bom usá-lo em instâncias pontuais.
Tudo bem.
Isso é algo que eu quase
posso prometer que você verá mencionado
no exame em algum lugar.
A disponibilidade de instâncias pontuais para
nós de tarefas.
Se você quiser reduzir os custos de um cluster
de EMR ou adicionar mais
capacidade de forma econômica, uma instância pontual é uma
ótima maneira de fazer isso, porque você não se importa
se ela cair, pois ela está sendo usada apenas
para obter capacidade
de processamento extra e o cluster pode
lidar com isso, se ela entrar ou
sair enquanto você estiver processando
seus trabalhos.
Não há risco de perda de dados com um nó de tarefa
porque ele não armazena dados.
Portanto, lembre-se novamente
de que uma boa maneira de expandir seu cluster
dinamicamente é usar uma instância local em um nó de tarefa.
Algumas maneiras de usar o EMR.
Portanto, uma delas é usar um cluster transitório.
Um cluster transitório será encerrado
automaticamente após a conclusão de todas
as etapas que lhe foram atribuídas.
Portanto, ao configurar um cluster transitório, você
pode dizer: "ok".
Quero que você ative esse cluster
de EMR que tem esse tipo de hardware por trás, e ele
executará essas etapas de processamento que
defini antecipadamente.
E, quando terminar, desligue-se.
Assim, você pode definir antecipadamente
as etapas no EMR que carregarão seus dados, processarão seus
dados e armazenarão os resultados.
E, quando terminar, desligue
automaticamente o cluster.
É disso que se trata um cluster transitório.
E, obviamente, isso economiza
dinheiro porque você não
está pagando pelo tempo nesse cluster além do que precisa.
Portanto, se você tiver esses tipos de trabalhos pontuais que
precisa executar de vez em quando, um cluster
transitório é uma boa maneira de fazer
isso, em que ele apenas
ativará esses recursos
de clusters, executará o trabalho e, em
seguida, será encerrado.
Portanto, é uma boa maneira de economizar dinheiro.
No entanto, às vezes você quer basicamente
criar um data warehouse de longa duração.
Você não quer ficar girando essa
coisa o tempo todo e desligando-a,
perdendo todos os seus dados
no processo, certo?
Portanto, se você quiser criar
basicamente um data warehouse
com processamento periódico em algum conjunto de dados grande,
no qual possa acessar esses dados sempre
que quiser ou executar trabalhos continuamente, um cluster de longa
duração pode ser mais adequado.
Portanto, nesse caso,
você criaria um cluster, com os parâmetros
que especificar antecipadamente,
e o deixaria em execução
para sempre.
Bem, não para sempre,
mas até que você o desligue manualmente.
E se você precisar adicionar capacidade
a ele mais tarde, poderá
sempre ativar mais nós de tarefa usando instâncias
pontuais para necessidades temporárias de capacidade
que você possa ter, como falamos.
Se quiser economizar ainda mais dinheiro, você pode
usar instâncias reservadas nesses clusters
de longa duração para economizar ainda mais.
Se você sabe que vai executar esse
cluster por muito tempo,
então, obviamente, uma instância reservada
é uma boa escolha para
o hardware que dá suporte a esse cluster.
Portanto, por padrão, a proteção de terminação estará ativada
e a terminação automática estará desativada em um cluster
de longa duração.
Ele tentará se preservar
o máximo possível.
Portanto, dois casos de uso aqui, clusters transitórios.
Se você quiser apenas ativar um cluster sob demanda,
execute algo que tenha predefinido e,
em seguida, desligue-o.
Ou um cluster de execução mais longa,
no qual você o mantém em execução o
tempo todo e pode acessá-lo
sempre que quiser e mantê-lo de maneira mais
persistente.
Você especifica as estruturas
e os aplicativos ao iniciar o cluster.
Então, falamos, por exemplo, sobre
a execução do Spark.
Isso seria algo que você selecionaria
quando estivesse girando o cluster
com antecedência,
e ele instalaria automaticamente
as estruturas e os aplicativos que
você deseja quando ele estivesse sendo
girado.
Depois de ter um cluster em funcionamento,
se for um cluster de longa duração, que
não esteja sendo executado apenas de forma
transitória, você poderá se conectar diretamente ao nó mestre e,
a partir desse nó mestre, executar seus
trabalhos diretamente.
Portanto, se você for uma pessoa que usa linha de comando,
basicamente, por exemplo, configuraria
um cluster de EMR habilitado para Spark.
Conecte-se ao nó mestre.
Inicie seu script de driver do Spark,
e ele fará seu trabalho usando
todo o poder do cluster.
Portanto, essa é uma maneira de usar o EMR.
Ou você pode enviar etapas por
meio do console da AWS para o EMR.
Portanto, essas etapas podem ser definidas estritamente
de forma gráfica por meio
do console, e você pode fazer
coisas básicas como processar
dados no S3 ou no HDFS, que é o sistema de arquivos
subjacente do Hadoop.
Você pode enviar esses dados para o S3 ou outro local, mas,
uma vez definidos,
poderá iniciar essas etapas
por meio do console do AWS em vez de passar
por um prompt de linha de comando por meio de
uma conexão direta com o nó mestre.
Portanto, há duas maneiras de usar o EMR: você
pode fazer login no nó mestre
e iniciar as coisas,
da maneira antiga.
Ou você pode definir suas etapas
usando exclusivamente o console e iniciar
essas etapas por meio do console para serem
executadas no cluster.
