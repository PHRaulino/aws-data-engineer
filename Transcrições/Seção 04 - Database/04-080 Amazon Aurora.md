Aurora porque o exame está começando
a fazer muitas perguntas sobre ele.
Agora, você não precisa de um conhecimento
profundo sobre
isso, mas precisa de uma visão geral de
alto
nível suficiente para entender exatamente
como ele funciona, portanto,
é isso que vou lhe dar nesta palestra.
O Aurora será uma tecnologia proprietária
da AWS.
Não é de código aberto.
Mas eles o tornaram compatível com
o PostgreSQL e o MySQL.
E, basicamente, seu banco de
dados Aurora terá drivers compatíveis.
Isso significa que, se você se conectar
como
se estivesse se conectando a um banco
de dados PostgreSQL ou MySQL, isso
funcionará.
O Aurora é muito especial, e não
vou me aprofundar muito nos aspectos
internos,
mas eles o otimizaram para a nuvem.
E, ao fazer muitas otimizações e coisas
inteligentes,
eles basicamente obtêm melhorias de
desempenho de 5x
em relação ao MySQL no RDS, ou
3x mais desempenho do PostgreSQL no RDS.
Não apenas isso, mas de várias maneiras
diferentes,
eles também obtêm mais melhorias de
desempenho.
Para mim, eu assisto, é muito, muito
inteligente, mas não vou entrar em
detalhes.
Agora, o armazenamento do Aurora cresce
automaticamente,
e eu acho que esse é um
dos principais recursos que é bastante
impressionante.
Você começa com 10 gigabytes, mas à medida
que coloca mais dados em seu banco de
dados, ele cresce automaticamente até 256
terabytes.
Novamente, isso tem a ver com a forma de
projetá-lo,
mas o mais incrível é que agora, como DBA
ou
SysOps, você não precisa se preocupar em
monitorar o disco,
pois sabe que ele crescerá automaticamente
com o tempo.
Ou posso ter até 15 réplicas de
leitura, e o processo de replicação será
mais rápido do que o MySQL.
Normalmente, você verá um atraso de
réplica inferior a 10 milissegundos.
Agora, se você fizer o failover
no Aurora, ele será instantâneo.
Portanto, será muito mais rápido do que um
failover do Multi-AZ no MySQL ou no RDS.
E como ele é nativo da nuvem,
por padrão, você obtém alta
disponibilidade.
Agora, embora o custo seja um pouco maior
do que o
do RDS, cerca de 20% a mais, ele é muito
mais
eficiente e, em escala, faz muito mais
sentido para a economia.
Então, vamos falar sobre os aspectos mais
importantes, que
são a alta disponibilidade e o
escalonamento de leitura.
Portanto, o Aurora é especial porque
armazenará
seis cópias de seus dados sempre que
você escrever algo em três AZ.
Assim, o Aurora é feito de forma a estar
disponível, de modo
que só precisa de quatro cópias de seis
para ser gravado.
Isso significa que, se um AZ estiver
inativo, você não terá problemas.
E você só precisa ter três cópias
das seis necessárias para a leitura.
Então, novamente, isso significa que ele
está altamente disponível para leituras.
Há algum tipo de processo de autocorreção
que
acontece, o que é muito legal, ou seja,
se alguns dados estiverem corrompidos ou
ruins, ele
faz a autocorreção com replicação ponto a
ponto
no backend, e isso é muito legal.
E você não depende de apenas um
volume, mas de centenas de volumes.
Novamente, não é algo que você possa
gerenciar,
pois isso acontece no back-end, mas isso
significa
que você simplesmente reduz o risco em
muito.
Portanto, se você observar do ponto de
vista
do diagrama, terá três AZs e um
volume de armazenamento compartilhado, mas
é um
volume lógico e faz replicação,
autocorreção e
expansão automática, o que representa
muitos recursos.
Portanto, se você escrever alguns dados,
talvez dados azuis,
verá as seis cópias deles em três AZ
diferentes.
Então, se você escrever alguns dados
laranja,
novamente, seis cópias deles em AZ
diferentes.
E, à medida que você escreve mais
e mais dados, eles basicamente vão para,
novamente, seis cópias em três AZ
diferentes.
O legal é que ele tem volumes
diferentes, é listrado e funciona muito
bem.
Agora precisamos saber sobre o
armazenamento e é isso.
Mas, na verdade, você não faz interface
com o
armazenamento, é apenas um design que a
Amazon
criou, e eu também quero apresentá-lo a
você,
para que você entenda o que Aurora exige.
Agora, o Aurora é como o Multi-AZ para
RDS.
Basicamente, há apenas uma instância que
recebe
gravações, portanto, há um mestre no
Aurora,
e é nele que receberemos as gravações.
E, se o mestre não funcionar, o failover
ocorrerá em menos de 30 segundos, em
média.
Portanto, é um failover muito, muito
rápido.
E, além do mestre, você
pode ter até 15 réplicas
de leitura, todas servindo leituras.
Portanto, você pode ter muitos deles, e é
assim
que você dimensiona sua carga de trabalho
de leitura.
Portanto, qualquer uma dessas réplicas de
leitura pode se
tornar o mestre em caso de falha do
mestre,
o que é bem diferente do funcionamento do
RDS.
Mas, por padrão, você tem apenas um
mestre.
O interessante dessas réplicas de leitura
é que
elas oferecem suporte à replicação entre
regiões.
Portanto, se você observar o Aurora
no lado direito do diagrama, é
disso que você deve se lembrar:
Um mestre, várias réplicas, e o
armazenamento será replicado, com
autocorreção, expansão
automática, blocos pequenos por blocos
pequenos.
Agora, vamos dar uma olhada em como o
Aurora está como um cluster.
Então, isso é mais sobre como o
Aurora funciona quando você tem clientes,
como
você faz a interface com todas essas
instâncias? Como dissemos, temos um volume
de
armazenamento compartilhado que está se
expandindo automaticamente.
Seu mestre é a única coisa
que escreverá em seu armazenamento.
E como o mestre pode mudar e sofrer
failover, o que o
Aurora oferece a você é o que chamamos de
endpoint de escritor.
Portanto, é um nome DNS, um ponto de
extremidade
de escritor, e está sempre apontando para
o mestre.
Portanto, mesmo que o mestre sofra uma
falha, seu
cliente ainda conversará com o endpoint do
escritor
e será automaticamente redirecionado para
a instância correta.
Agora, como eu disse antes, você
também tem muitas réplicas de leitura.
O que eu não disse é que eles podem
ter escalonamento automático em cima
dessas réplicas de leitura.
Portanto, você pode ter de uma a 15
réplicas de
leitura e pode configurar o
dimensionamento automático, de modo que
sempre tenha o número certo de réplicas de
leitura.
Agora, como você tem escalonamento
automático, pode ser
muito, muito difícil para seus aplicativos
acompanhar onde
estão suas réplicas de leitura, qual é o
URL, como faço para me conectar a elas.
Portanto, para isso, você precisa se
lembrar
disso para fazer o exame: Existe algo
chamado ponto de extremidade do leitor.
E um ponto de extremidade de leitor tem
exatamente o
mesmo recurso que um ponto de extremidade
de escritor.
Ele ajuda no balanceamento de carga da
conexão e
se conecta automaticamente a todas as
réplicas de leitura.
Portanto, sempre que o cliente se conectar
ao ponto de extremidade
do leitor, ele será conectado a uma das
réplicas de
leitura, e o balanceamento de carga será
feito dessa forma.
Observe que o balanceamento de carga
ocorre no nível da conexão,
não no nível do comando.
Portanto, é assim que funciona para a
Aurora.
Lembre-se do ponto de extremidade do
escritor e do ponto de extremidade do
leitor.
Lembre-se do dimensionamento automático.
Lembre-se do volume de armazenamento
compartilhado que se expande
automaticamente.
Lembre-se deste diagrama porque, depois de
obtê-lo,
você entenderá como o Aurora funciona.
Agora, se nos aprofundarmos nos recursos,
você terá
muitas coisas que eu já lhe disse:
failover
automático, backup e recuperação,
isolamento e segurança,
conformidade com o setor, dimensionamento
por botão
de pressão por meio de dimensionamento
automático.
Aplicação automatizada de patches sem
tempo de inatividade, por isso
é muito legal a mágica que eles fazem no
back-end.
Monitoramento avançado, manutenção de
rotina.
Portanto, todos esses aspectos são
tratados para você.
E você também tem esse recurso
chamado backtrack, que permite restaurar
dados a qualquer momento e,
na verdade, não depende de
backups, mas de algo diferente.
Mas você sempre pode dizer: "Quero voltar
para ontem às 16h". E você diz:
"Ah, não, na verdade eu queria fazer
ontem às 17h". E isso também funcionará,
o que é muito, muito legal.
Então é isso para Aurora, e
eu os vejo na próxima palestra.
