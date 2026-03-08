do EMR, o EMR Serverless.
Funciona praticamente com a mesma ideia do EMR.
A diferença é que a etapa intermediária de
definir a capacidade de que precisamos foi removida
de nós.
Assim, podemos deixar que o EMR decida por si mesmo quantos
nós são necessários no cluster para realmente
fazer o que queremos que ele faça automaticamente.
Portanto, para usar o EMR Serverless, basta
começar escolhendo a versão e o tempo de execução do
EMR, Spark, Hive ou Presto, exatamente como faríamos antes.
Depois, basta enviar consultas e scripts para
nossa instância EMR Serverless por meio de uma solicitação de execução de trabalho.
Assim, em vez de fazer login diretamente no nó mestre, ele é sem servidor,
portanto, você só quer
interagir com ele indiretamente.
Você dará a ele um caminho para alguma coisa do S3 em algum lugar
que diga que é aqui que está o meu script.
Ele fará referência aos dados do S3, e basta alimentar
o script ou a consulta do Hive no S3 para o servidor sem servidor,
e ele automaticamente, em teoria, descobrirá
a capacidade necessária para
executar o trabalho com sucesso.
Portanto, o EMR gerenciará a capacidade subjacente para você,
mas se você quiser pensar sobre a capacidade subjacente,
ainda poderá fazê-lo, e isso pode ser uma
boa ideia em muitas situações.
Portanto, se você sabe que seu trabalho exige muitos recursos, pode especificar
isso antecipadamente.
Você pode especificar antecipadamente os tamanhos padrão dos workers
e também pode pré-inicializar sua capacidade.
Portanto, em vez de começar do nada, você
pode dizer ao EMR Serverless:
"Ei, acho que a capacidade básica de que vou precisar
é esta quantidade de nós deste tamanho" e começar
a partir daí.
Isso o ajudará.
Caso contrário, ele tentará calcular isso para você automaticamente.
E mesmo que você comece com uma configuração
básica de uma capacidade pré-inicializada, ele analisará os recursos que são realmente
necessários para o seu trabalho
e os ajustará de acordo, programando
os funcionários conforme a necessidade e desprogramando-os
quando não forem necessários.
No momento, tudo funciona na mesma região, em várias
zonas de disponibilidade, é claro, portanto,
seu cluster sem servidor estará em uma região.
Então, por que isso é tão importante?
Bem, você não precisa mais descobrir quantos
funcionários precisa, certo?
Portanto, um ponto realmente problemático em coisas como o Apache Spark é que,
se você adivinhar muito pequeno, se
não tiver recursos suficientes para um trabalho, acabará
ficando sem memória.
Seu trabalho falhará no meio do caminho.
E pode ser um processo muito demorado
e caro descobrir a capacidade de que
realmente preciso, porque não
é uma maneira muito boa de descobrir
isso com antecedência.
Portanto, o EMR Serverless está resolvendo esse problema.
Isso é realmente impressionante, se você quer saber.
Você provisionará automaticamente a capacidade
necessária para o seu trabalho e não precisará se preocupar com isso, o que é realmente
muito importante.
Você pode se concentrar nos
scripts e no que está tentando fazer, em vez de descobrir a
capacidade necessária para isso.
E, como eu disse, ele não é realmente sem servidor como alguns
outros servidores sem servidor,
nos quais você realmente não pensa nos servidores.
Nos bastidores, você ainda está usando o Spark, o Hive ou o Presto,
e essas tecnologias pressupõem que você
tenha algum conhecimento
do que está acontecendo no nível do nó de trabalho
ou no nível do driver, certo?
Portanto, se você ainda quiser configurar o Spark nesse nível, ainda terá
que pensar nos nós de trabalho e em
suas capacidades.
A diferença é que você não sabe necessariamente
quantos deles você tem e não sabe necessariamente
onde eles estão.
Como faço para usar o EMR Serverless?
Bem, você começa com um usuário
IAM com o qual vai interagir, e isso funcionará
com a CLI do AWS.
Portanto, seu usuário invocará a CLI para
criar esse cluster sem servidor.
Por enquanto, somente a CLI é compatível.
Tenho certeza de que isso mudará muito em breve.
Não consigo imaginar que eles não tenham
suporte para console e SDK no futuro, mas, por
enquanto, é apenas uma interface de linha de comando.
Em seguida, você precisa configurar uma função de execução
de trabalho no IAM para o trabalho em si.
E isso garante que seu trabalho tenha permissão
para acessar o Amazon AWS EMR Serverless, bem como todas as permissões
necessárias para acessar seus
scripts no S3 e todos os dados que ele
precisa acessar no S3.
Se você estiver fazendo algo com o SparkSQL,
talvez precise acessar o Glue para obter metadados do Glue ou quaisquer
chaves KMS necessárias para qualquer segurança que você tenha
configurado.
Com isso em mãos, você pode criar um aplicativo EMR sem
servidor usando o Spark, o Hive, o que quiser, e então alimentá-lo
em seu trabalho por meio de uma solicitação
de trabalho EMR.
Assim, você fornece a ele um link para o script do Spark, a consulta
do Hive, seja qual for, que pode ser assim.
Portanto, aqui está um exemplo de uma linha
de comando para invocar um trabalho EMR Serverless.
Estamos apenas dizendo AWS EMR serverless start job run, passando
nosso ID de aplicativo, a função de execução sobre a qual falamos
anteriormente, com um caminho para isso.
E, em seguida, no driver de trabalho, é aí
que as coisas ficam interessantes.
Estamos dizendo que, no Spark submit,
o ponto de entrada é esse caminho para o próprio script.
Também podemos passar argumentos para esse ponto de entrada
se quisermos um parâmetro para onde ele
deve colocar sua saída, por exemplo.
E também podemos substituir os parâmetros
de envio do Spark.
Portanto, se você quiser enviar parâmetros ao próprio Spark
na linha de comando do Spark submit, poderá
especificar isso aqui também.
Então, novamente, mesmo que estejamos chamando
isso de sem servidor, ainda estou pensando no tamanho dos núcleos do meu executor, como são
os núcleos do meu driver, coisas assim.
Portanto, você ainda tem esse nível de controle
aqui, mesmo que esteja transferindo a capacidade
real e a quantidade de nós para o EMR Serverless.
Além disso, você pode enviar substituições de configuração
que são específicas do EMR Serverless.
Neste exemplo, estamos dizendo
que queremos enviar nossos logs do CloudWatch para este caminho no S3.
Quando terminamos, recebemos nossos resultados em nossos registros, onde
quer que tenhamos dito para colocá-los.
E é isso.
Basta encerrá-lo quando
terminar e ele será como um EMR.
Vamos falar rapidamente sobre o ciclo de vida
de um aplicativo EMR sem servidor.
Portanto, você começa criando explicitamente seu aplicativo
por meio de um comando, atualmente a partir da CLI.
Se isso for bem-sucedido, ótimo, você criou seu aplicativo.
Caso contrário, ele será encerrado automaticamente.
A partir desse ponto, você terá um novo aplicativo
que criou.
Você pode optar por rescindi-lo imediatamente.
Essa é uma opção. Não sei por que você
faria isso, mas, normalmente, você emitiria um comando start para
iniciar o aplicativo, o que daria início
a ele e o executaria de fato.
Uma vez iniciada, ela será bem-sucedida e passará
para a fase de parada quando você terminar,
ou falhará e passará para
a fase de parada automaticamente.
Depois que ele for interrompido com
êxito, você poderá executá-lo novamente,
voltar para o início ou ir para a fase finalizada
e encerrá-lo quando terminar.
Quero enfatizar que nem tudo isso
está acontecendo automaticamente.
Preciso chamar comandos por meio da API, como CreateApplication,
StartApplication, StopApplication
e, quando terminar, DeleteApplication, para
que tudo isso aconteça.
Então, alguns alunos entraram em contato
comigo dizendo: "Ei, você sabe que usa o EMR em muitos dos seus cursos
e está sempre nos avisando para lembrar
de fechar o cluster quando terminar,
para não ser cobrado por ele inesperadamente.
Devo usar apenas o EMR Serverless
para não ter que pensar nisso? Não, isso não resolve
o problema.
Isso ajuda porque você automaticamente não usará
mais capacidade do que precisa, mas ainda precisará
excluir explicitamente o aplicativo
quando terminar de usá-lo.
Se você se esquecer de fazer isso, ainda será cobrado por
esse aplicativo sem servidor, mesmo
que ele não esteja fazendo nada, certo?
Portanto, não pense que o EMR Serverless é uma desculpa para ser preguiçoso
no gerenciamento de seus recursos.
Você ainda precisa pensar em iniciar, parar e encerrar
explicitamente esse cluster quando terminar.
O EMR Serverless significa apenas que ele está
pensando na capacidade em vez de você, mas
você ainda precisa gerenciar essa capacidade
até certo ponto.
Vamos falar um pouco mais a fundo sobre a capacidade
pré-inicializada no EMR Serverless.
Portanto, aqui está um exemplo à direita
de como isso pode parecer na linha de comando.
Você vê que temos um bloco de capacidade inicial
que não tínhamos antes.
Estamos dizendo que queremos começar com cinco drivers
com uma configuração de recursos específica de
um tipo de CPU e a memória que cada um tem disponível.
Além disso, para os nós executores, estamos dizendo
que queremos 50 deles para começar com quatro VCPUs
cada um e oito gigabytes por executor também.
Então, você sabe disso, digamos quantos processos
eu quero para alimentar meu aplicativo.
Ainda é tarefa do EMR Serverless descobrir onde esses processos
estão sendo executados e a capacidade
necessária para que isso realmente aconteça.
Mas você pode dar uma dica como esta para
dizer: "Ei, eu sei que este é um trabalho bastante exigente.
Quero começar com 50 executores.
Vá descobrir como fazer isso acontecer.
Mas, para que tudo ocorra de forma mais tranquila
e para garantir que eu tenha capacidade suficiente desde o início,
quero que você comece a partir deste ponto. Há também um argumento de
capacidade máxima sendo
enviado aqui.
Quero dizer que não quero usar mais do que 400
CPUs virtuais e não mais do que um terabyte de memória.
Portanto, essa é uma boa proteção para o caso
de você fazer algo bobo que
queira usar recursos infinitos.
Isso será uma pequena rede de segurança para você.
Uma observação da documentação,
e isso parece ser o tipo de coisa
que eu poderia imaginar ver no exame em algum momento.
Lembre-se de que o Spark adiciona uma sobrecarga de 10% a qualquer
memória solicitada para drivers e executores.
Portanto, certifique-se de que sua solicitação inicial de capacidade
leve isso em consideração.
Certifique-se de que esteja solicitando pelo menos 10% a mais de memória do que
o seu trabalho está realmente solicitando.
Algumas observações sobre segurança com o EMR Serverless.
É praticamente a mesma coisa que EMR.
Para o armazenamento, se você estiver usando
o EMRFS sob o capô, esse é o S3.
Portanto, você sabe que a criptografia do lado do serviço ou
do lado do cliente no S3 em repouso estará disponível para você.
Para o trânsito, o TLS estará presente
para você entre os nós EMR e o S3.
Se você estiver gravando diretamente
no S3, obviamente toda a segurança
que vem com o S3 também
estará disponível para você, SSE-S3, SSE-KMS, o que você quiser usar.
Para qualquer armazenamento efêmero nos discos locais dos
seus nós, eles também são criptografados.
E, em trânsito, qualquer comunicação entre os nós do driver e os
executores também é criptografada automaticamente.
Se você estiver usando o Hive, qualquer comunicação
entre o Glue Metastore e o EMR
também será criptografada em trânsito usando TLS.
E uma observação rápida da documentação
que eu gostaria de passar adiante.
Lembre-se de que, se estiver usando o
S3, você poderá forçar o HTTPS no tráfego em trânsito para
o S3 usando a política AWS SecureTransport.
Outra abordagem sem servidor para o EMR é o EMR no EKS.
Esse é o Elastic Kubernetes Service.
Portanto, se o seu mundo é construído em torno do
Kubernetes, e isso é verdade para muitas pessoas
atualmente, essa é uma maneira de usar o EMR e o Spark em particular,
dentro do EKS, dentro do Amazon EKS.
Portanto, isso permite que você envie um trabalho
do Spark no Elastic Kubernetes Service sem ter que se preocupar com
o provisionamento dos clusters para ele.
Portanto, isso lhe dá todos os benefícios do Kubernetes,
em vez de apenas ter um cluster EMR autônomo, e também lhe dá
os benefícios de todos os aspectos
totalmente gerenciados do EMR, certo?
Assim, você não precisa lidar com a configuração
de seu próprio aplicativo Spark no EKS, pois isso automatiza
tudo para você.
Portanto, trata-se de uma solução totalmente gerenciada
para o Elastic MapReduce e, em particular, para o Spark, sobre o seu mundo EKS.
A vantagem de fazer isso é que você pode compartilhar recursos
entre o Spark e outros aplicativos que você possa ter em
execução no Kubernetes.
Portanto, esse diagrama à direita mostra isso.
Temos o EMR no EKS na parte superior, passando pelo EKS, e você pode ver
como um aplicativo Spark é apenas uma
das muitas coisas que você está fazendo
nesse cluster EKS, certo?
Assim, você pode ter outros aplicativos fazendo
coisas totalmente diferentes, talvez um aplicativo de análise.
Você pode até ter versões diferentes
do Spark em execução junto com todo o resto.
E, com a magia do Kubernetes, podemos compartilhar
esses recursos com mais eficiência.
Portanto, essa pode ser uma maneira melhor de usar o hardware
que você tem e, por fim, economizar dinheiro.
E você sabe, também vemos que ele tem todas essas integrações
com outros serviços da Amazon na parte inferior, espalhadas potencialmente
entre várias zonas de disponibilidade.
Novamente, você não precisa se preocupar muito com isso.
Com apenas alguns cliques no console, você
pode escolher a versão do Apache Spark que deseja, implantar
uma carga de trabalho do EMR no Amazon EKS, o EMR empacotará
automaticamente essa carga de trabalho em
um contêiner e fornecerá esses conectores pré-criados para integração
com esses outros serviços da AWS.
O EMR implantará o contêiner no cluster EKS e gerenciará todo o dimensionamento,
o registro em log e o monitoramento dessa carga
de trabalho para você.
