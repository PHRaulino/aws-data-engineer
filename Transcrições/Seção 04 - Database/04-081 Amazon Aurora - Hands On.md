de dados do Amazon Aurora.
Agora, só para que você saiba, se você me
acompanhar
nessa prática, isso vai lhe custar um
pouco de dinheiro.
O mais importante para você é apenas
seguir
as instruções e ver quais são as opções.
Mas você não precisa realmente ir em
frente e criar o banco de dados
se não tiver dinheiro para isso.
Portanto, vamos escolher uma criação
padrão.
E, como você pode ver, temos duas opções
diferentes para o Aurora: a opção
compatível com
MySQL e a opção compatível com
PostgresSQL.
Para esta prática, usarei o MySQL.
Vou rolar a tela para baixo e aqui você
terá que escolher uma versão.
Portanto, você tem um seletor de versão
bem aqui.
E você pode ter filtros, por exemplo, para
mostrar
apenas a versão que oferece suporte ao
recurso
de banco de dados global, ou as que
oferecem suporte ao recurso de consulta
paralela ou
as que oferecem suporte ao recurso
Serverless v2.
Portanto, o que vou fazer é manter
a versão padrão proposta pelo console
do Aurora, que é a 3.04.1.
Mas essa pode ser uma versão diferente
para você.
Em seguida, escolherei um modelo
e, basicamente, a escolha da
produção me permite configurar tudo.
Portanto, é isso que queremos fazer.
Escolheremos a produção.
Para o identificador do cluster de banco
de dados
no RDS, escolheremos o banco de dados
dois.
O nome de usuário principal é admin
e, em seguida, você pode inserir
uma senha, o que farei agora.
Então, para a configuração do
armazenamento
em cluster, você tem duas opções.
Você pode ter o Aurora padrão ou otimizado
para IO.
Portanto, se você tiver muitas operações
de entrada e
saída, operações de leitura e gravação no
banco de
dados do Aurora, talvez queira otimizar o
IO.
Mas para cargas de trabalho econômicas que
não usam muito o Aurora, talvez
você queira usar o Aurora padrão.
Agora, para a configuração da instância,
você tem
a possibilidade de escolher a classe de
instância
que deseja para o seu banco de dados.
Assim, você pode ver que há diferentes
tipos
que podem ser otimizados para a memória.
Você tem as classes expansíveis e pode
optar por incluir as classes da geração
anterior, o que às vezes funciona.
Mas, por enquanto, usarei apenas a mídia
db.t3.
Além disso, se você usar uma
versão compatível com serverless, verá a
opção Serverless v2 two aqui.
E aqui você não seleciona o tipo de
instância, apenas
seleciona o que é chamado de unidade de
capacidade
Aurora, ACU, e diz, bem, há uma ACU mínima
que você quer e uma ACU máxima que você
quer, e isso permitirá que seu banco de
dados
seja dimensionado entre essas duas
unidades de capacidade automaticamente.
Portanto, por enquanto, usarei as
classes burstable da mídia db.t3.
Agora, em termos de disponibilidade e
durabilidade, temos
a opção de ter réplicas da Aurora.
Portanto, aqui criamos uma réplica do
Aurora
e um nó de leitura em uma
AZ diferente, o que nos dará
disponibilidade, disponibilidade
aprimorada, bem como leituras
melhores na AZ e failovers rápidos.
Portanto, isso custará mais dinheiro, mas
pelo menos poderei
mostrar a você todo o poder do Aurora.
Em seguida, para o recurso de computação,
não
vamos nos conectar a um recurso EC2.
Vamos escolher um tipo de rede IPv4, que
será suficiente para nossas necessidades,
mas se
você também tiver IPv6 em sua VPC,
poderá usar o modo de pilha dupla.
Então você estará na VPC.
Essa é a VPC padrão com o grupo de envio
padrão.
Sim, permitirei o acesso público para
permitir o acesso ao banco
de dados do Aurora a partir de um IP
público.
E para o grupo de segurança VPC, vou criar
um novo
grupo e chamá-lo de banco de dados de
demonstração Aurora,
que nos permitirá conectar ao nosso banco
de dados Aurora.
Em seguida, para configuração adicional,
podemos ver que
a porta do banco de dados é
3306, que é a porta do MySQL.
Se você tiver selecionado MySQL antes.
Portanto, temos a opção de também ter
encaminhamento de gravação
local, caso os direitos sejam aplicados à
réplica de leitura.
Em seguida, eles serão encaminhados
automaticamente
para a instância de gravação.
Isso permite que você tenha um
gerenciamento de conexão mais fácil.
Agora, também podemos ter autenticação de
banco de
dados, para usar o aplicativo de banco de
dados baseado em IAM ou Kerberos para
basicamente
autenticar um usuário usando um mecanismo
externo.
Temos um monitoramento aprimorado.
Posso desativá-lo porque não precisamos
dele.
E temos opções adicionais para seu banco
de dados.
Por exemplo, o nome inicial do banco de
dados será my
DB e a retenção do backup será de um dia.
Isso é ótimo.
Podemos ter criptografia para nosso banco
de dados.
Temos várias opções de retrocesso para
retroceder
nosso banco de dados e exportações
de registros, mas não vou examiná-las.
Temos proteção contra exclusão para evitar
que
o banco de dados seja excluído
acidentalmente,
mas tudo parece estar bem agora.
E, como você pode ver, temos alguns custos
mensais.
Portanto, certifique-se de que você está
ciente disso
ao criar esse banco de dados do Aurora.
Então, vamos criar esse banco de dados.
Assim, meu banco de dados do Aurora foi
criado.
E, como podemos ver, temos um cluster
regional com
uma instância de escritor e uma instância
de leitor.
Portanto, aqui, o fato importante é que
temos instâncias diferentes para escrever
e ler,
e elas estão em AZ diferentes.
Portanto, esse é todo o poder do Aurora.
Portanto, se você clicar no banco de dados
dois, como
podemos ver para conectar, teremos dois
pontos de extremidade.
Temos um ponto de extremidade de leitor e
um ponto de extremidade de escritor.
Portanto, esses pontos de extremidade são
muito úteis
porque representam um ponto de extremidade
que
sempre levará à instância correta do
escritor.
E esse ponto de extremidade sempre
levará à instância correta do leitor.
Portanto, esses pontos de extremidade são
o que seu
aplicativo deve usar para se conectar ao
Aurora.
Mas se você clicar diretamente
nessa instância específica aqui, ela
também terá um endpoint dedicado.
E essa instância aqui também teria um
endpoint dedicado quando estivesse sendo
criada.
Portanto, ainda é preciso estar no espaço
de criação.
Então, temos esses recursos que são
legais.
Além disso, temos outros recursos, de modo
que
podemos adicionar mais leitores ao nosso
cluster de
leitores para aumentar a capacidade de
dimensionamento.
E também podemos criar uma réplica de
leitura entre regiões
se você quiser ter uma réplica em outra
região.
Podemos restaurar em um ponto no tempo.
E outra é que poderíamos adicionar o
dimensionamento automático de réplicas.
Portanto, isso é muito importante porque,
bem, podemos criar uma política.
E essa política diria: "Ei, com base na
utilização média de sua réplica do Aurora
ou
no número médio de conexões com sua
réplica
do Aurora, dimensione sua réplica de
leitura".
Portanto, leia a política de
dimensionamento de réplicas.
E dizer, ok, quero ter certeza de que
minha
réplica de leitura permaneça no valor-alvo
de 60%.
E se eu ultrapassar, por favor, crie mais
réplicas de leitura.
Também poderíamos definir um período de
escalonamento para
a política de escalonamento, o que faz
sentido.
E qual é a capacidade mínima e máxima.
Portanto, uma réplica até 15 réplicas do
Aurora.
E isso é muito útil para ter uma réplica
de
leitura em escala automática como um banco
de dados.
Então, eu o cancelei, pois não precisamos
dele no momento.
E agora eu me certifiquei de que meus
pontos,
meu banco de dados e endpoints estão
disponíveis.
Portanto, estamos prontos para ir.
Portanto, uma última coisa que posso fazer
para mostrar
a você todo o poder do Aurora é realizar
uma ação e adicionar uma região da AWS.
E isso só é possível se você escolher uma
versão do Aurora
que tenha sido ativada com o recurso de
banco de dados global.
Mas aqui podemos adicionar a região do
banco de dados a
outras regiões, e isso permitirá que você
obtenha uma Aurora global.
Agora, como você pode ver, isso não é
possível com esse cluster porque
precisamos ter uma
instância com tamanho compatível para
fazer isso primeiro.
Portanto, precisamos alterar a instância,
por exemplo,
para um tipo de instância grande,
e então poderemos adicionar outras regiões
ao cluster do banco de dados.
Mas, de qualquer forma, eu queria mostrar
a você o recurso aqui.
Ok, então é isso para a Aurora.
Isso é basicamente o que você obtém, que é
um banco de dados incrível com desempenho
incrível,
grande capacidade de dimensionamento,
global e sem servidor.
Portanto, um banco de dados muito, muito
completo.
Eu realmente gosto dessa oferta da AWS.
Agora, para terminar com essa prática,
basta pegar
esse banco de dados e excluí-lo, mas, como
você pode ver, ele não está disponível.
Portanto, o que você precisa fazer
primeiro
é excluir a instância do leitor.
Portanto, digite delete me.
Em seguida, você precisa excluir a
instância do escritor.
Então, novamente, ação, excluir e, em
seguida, você digita excluir-me.
E, depois que essas duas coisas forem
excluídas, você poderá excluir todo o
cluster.
Portanto, esperarei quando estiver pronto.
É isso aí.
Meu banco de dados foi excluído e
eu o verei na próxima palestra.
