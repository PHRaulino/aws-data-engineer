a outros serviços do AWS?
Bem, vamos examinar alguns deles.
Assim, no Amazon S3, você pode usar o
processamento paralelo para exportar seus
dados do Amazon
Redshift para vários arquivos de dados no
S3.
E, é claro, você também pode importar
dados do S3 ou
até mesmo trabalhar em cima deles usando o
Amazon Redshift.
Amazon DynamoDB, portanto, ao usar o
comando copy, você
também pode carregar uma tabela do
Redshift com
dados de uma única tabela do Amazon
DynamoDB.
Portanto, também é possível importar dados
do DynamoDB
para o Redshift usando o comando copy.
Em hosts EMR ou instâncias EC2,
você pode importar dados usando SSH.
Portanto, novamente, por meio do comando
copy, você
pode carregar dados de um ou mais
hosts remotos, como clusters EMR ou o
que quer que esteja executando no EC2.
E, por fim, o AWS Database Migration
Service ou
DMS pode migrar seus dados para o Amazon
Redshift
para você ou, pelo menos, ajudá-lo com o
processo.
Portanto, o serviço de migração de banco
de dados é um tópico totalmente grande.
Basicamente, é um conjunto de ferramentas
que
permite que você migre dados de algum
data warehouse existente para o Amazon
Redshift.
E, muitas vezes, há muito mais do que você
imagina.
Além disso, o Redshift também pode se
comunicar
com o AWS Glue para o Apache Spark.
Por trás disso, ele usa o S3 e comandos
de cópia para mover dados para frente e
para
trás, mas você também pode ler e gravar em
tabelas do Redshift por meio do AWS Glue.
Você também precisará saber, pelo menos, o
que
é o Redshift Workload Management,
abreviado como WLM.
É uma maneira de ajudar os usuários a
priorizar as cargas
de trabalho para que as consultas curtas e
de execução rápida
não fiquem atrás de consultas lentas e de
execução demorada.
A maneira como funciona é criando filas de
consulta em
tempo de execução de acordo com as classes
de serviço.
E os parâmetros de configuração para
vários tipos de
filas são definidos por essas classes de
serviço.
Agora, é possível modificar a configuração
do WLM para
criar filas separadas para consultas de
longa duração e
para consultas de curta duração,
melhorando assim o
desempenho do sistema e a experiência do
usuário.
Você pode configurar tudo isso usando o
Console de Gerenciamento do Amazon
Redshift, a
Interface de Linha de Comando do Amazon
Redshift ou a API do Amazon Redshift.
O tópico de dimensionamento e ajuste do
cluster Redshift também aparece bastante
no exame.
Um recurso que você precisa conhecer
é o chamado escalonamento de
simultaneidade.
Esse recurso permite que você adicione
automaticamente
a capacidade do cluster para lidar com
aumentos repentinos nas consultas de
leitura simultâneas.
Portanto, se você tiver um acesso muito
intenso
ao seu cluster do Redshift, no qual há
uma inundação repentina de consultas de
leitura vindas
de fora, o dimensionamento de
simultaneidade poderá dimensionar
automaticamente o cluster para lidar com
isso.
Dessa forma, ele pode oferecer suporte a
consultas e usuários simultâneos
praticamente ilimitados.
Ele continua adicionando mais e mais
capacidade, conforme necessário, à
medida que suas consultas de leitura
aumentam de volume.
E você pode usar filas de gerenciamento de
carga de trabalho, sobre as quais
falaremos novamente
em breve, para gerenciar quais consultas
são
enviadas ao cluster de dimensionamento de
simultaneidade.
Assim, você pode gerenciar, por meio da
fila à qual atribui suas consultas,
quais delas podem realmente aproveitar o
dimensionamento da simultaneidade e quais
não.
Isso pode permitir que você, por exemplo,
separe as consultas de leitura que você
acha que podem ser de natureza explosiva
ou variar no tempo e na
frequência, e use isso para dimensionar
automaticamente a capacidade dessa
consulta específica.
Isso reduz o risco de, inadvertidamente,
adicionar um monte de capacidade para
algum trabalho off-line que não precisa
necessariamente ser executado com rapidez.
Assim, você pode escolher quais consultas
aproveitam o escalonamento da
simultaneidade.
Obviamente, isso não é gratuito, portanto,
é preciso pensar um pouco sobre
quais consultas podem realmente ter esse
recurso de adicionar automaticamente mais
e mais capacidade conforme necessário.
O gerenciamento de carga de trabalho, WLM,
é oferecido em algumas variantes
diferentes.
Um deles é chamado de gerenciamento
automático de carga de trabalho.
Assim, com o gerenciamento automático da
carga
de trabalho, você pode definir até oito
filas diferentes que são gerenciadas para
você.
E, por padrão, você tem cinco filas que
têm uma alocação de memória uniforme entre
elas,
mas você pode alterar isso, obviamente, se
precisar.
Portanto, a ideia é que, se você
tiver várias consultas grandes em uma
fila,
como grandes junções de hash ou
algo do tipo, a simultaneidade será
reduzida automaticamente nessa fila para
você.
E se houver várias consultas pequenas em
uma
fila, como inserções, varreduras ou
agregações simples, o
nível de simultaneidade nessa fila poderá
ser elevado.
A simultaneidade é a quantidade de
consultas que
posso executar ao mesmo tempo, certo?
Portanto,
consultas maiores obviamente precisam de
mais capacidade.
Talvez você queira diminuir a
simultaneidade dessas consultas para
que elas recebam mais recursos, enquanto
as consultas
pequenas podem ser feitas com menos
recursos e
você pode executar mais delas ao mesmo
tempo.
Ao separar essas consultas em suas
próprias filas,
podemos aproveitar melhor o hardware que
temos.
Portanto, cada fila de consulta de carga
de trabalho
automática pode ser configurada de várias
maneiras diferentes.
Uma coisa que você pode fazer é definir um
valor de prioridade, que apenas define a
importância
relativa das consultas em uma carga de
trabalho.
Você também pode definir o modo de
escalonamento da simultaneidade.
Basicamente, foi sobre isso que falamos
anteriormente com o escalonamento da
simultaneidade.
É aqui que você pode dizer: quero que
essa fila específica tenha acesso a um
cluster
de escalonamento de simultaneidade e tenha
a capacidade
de adicionar automaticamente mais e mais
recursos, mais
e mais servidores sob o capô para lidar
com a capacidade de que essa fila precisa.
Isso custa dinheiro, obviamente, portanto,
você deve pensar cuidadosamente se
isso é possível ou não.
Também é possível atribuir um conjunto de
grupos
de usuários a uma fila, especificando um
nome
de grupo de usuários ou usando curingas.
Portanto, quando um membro de um grupo
de usuários listado executa uma consulta,
essa
consulta será executada automaticamente na
fila correspondente.
Portanto, você pode atribuir filas a filas
de consulta com base nos usuários.
Você também pode configurar um grupo de
consulta. Tudo o que você precisa é de um
rótulo.
Então, basicamente, em tempo de execução,
você pode atribuir um
rótulo de grupo de consultas a uma série
de consultas,
e isso definirá em qual fila essa consulta
será colocada.
Então, basicamente, uma tag, um rótulo
atribuído à própria consulta pode definir
para qual fila ela vai.
Você também pode configurar regras de
monitoramento de consultas.
São muito legais.
Eles permitem que você defina limites de
desempenho baseados em
métricas para filas de gerenciamento de
carga de trabalho.
E você pode especificar a ação a ser
tomada quando uma consulta ultrapassar
esses limites.
Assim, por exemplo, você pode ter uma fila
dedicada a consultas de curta duração e
pode ter uma regra de monitoramento de
consultas que aborte essas consultas se
elas
forem executadas por mais de 60 segundos.
Dessa forma, você pode garantir que sua
fila de
consultas curtas esteja realmente tratando
de consultas curtas.
E se algo der errado com uma dessas
consultas, isso
não vai atrasar todas as outras consultas
na fila.
Portanto, essa é uma ferramenta muito
útil.
Você também pode fazer coisas como
transferir as
consultas para uma fila diferente se elas
violarem alguma regra de monitoramento de
consultas.
A outra variante do WLM é o gerenciamento
manual da
carga de trabalho e, por padrão, ele vem
com
uma fila com um nível de simultaneidade de
cinco.
Novamente, o nível de simultaneidade é a
quantidade de consultas
que podem ser executadas ao mesmo tempo
nessa fila.
Além disso, há uma fila de superusuário
com um nível de simultaneidade de um.
Essa é uma fila destinada a consultas
administrativas que estão acontecendo
e que sempre devem ser executadas, não
importa o que aconteça.
Você pode definir até oito filas manuais e
pode ter
um nível de simultaneidade em uma fila de
até 50.
Cada uma dessas filas permite que você
defina
se o cluster de escalonamento de
simultaneidade
está disponível ou não, se ele pode
adicionar automaticamente mais capacidade
a essa fila.
Você também pode definir um nível de
simultaneidade
manual para essa fila, definindo quantas
consultas eu
quero poder executar de uma vez dentro
dela.
Você pode atribuir grupos de usuários a
ele
e grupos de consultas, como falamos
anteriormente com
as filas automáticas, permitindo que você
encaminhe automaticamente
as consultas para uma fila com base no
usuário que a está executando ou no rótulo
de consulta que foi anexado à consulta.
Você também pode definir a memória alocada
para uma determinada fila,
o valor de tempo limite para executar uma
consulta nessa fila.
E, novamente, todas as regras de
monitoramento de consultas que você possa
ter.
Você também pode ativar o que é chamado de
salto de fila de consulta.
Portanto, se uma consulta atingir o tempo
limite
em uma determinada fila, você poderá
configurá-la para
que passe para a próxima fila e tente
novamente em uma fila diferente que possa
ter
um tempo limite maior ou mais recursos
disponíveis.
Outro aspecto a ser abordado aqui é
a aceleração de consultas curtas ou SQA.
A ideia aqui é priorizar automaticamente
as consultas de execução
curta em detrimento das consultas de
execução mais longa.
As consultas curtas serão executadas em
seu próprio
espaço dedicado para que não fiquem
esperando em
uma fila atrás de consultas mais longas.
Portanto, isso pode ser usado no lugar das
filas de gerenciamento
de carga de trabalho se você quiser apenas
acelerar consultas curtas.
Ele pode funcionar com instruções CREATE
TABLE AS. Lembre-se disso.
E também consultas somente leitura ou
instruções SELECT.
Portanto, ambos são candidatos à
aceleração de consultas curtas.
Ele pode executá-las automaticamente em
seu próprio espaço para que
não fiquem presas atrás de consultas
analíticas mais longas.
E ele funciona usando aprendizado de
máquina. Muito legal.
Portanto, ele tenta prever automaticamente
o tempo de execução
de uma consulta usando algoritmos de
aprendizado de máquina.
Assim, ele pode adivinhar, com base na
própria
consulta, quanto tempo ela pode levar e
descobrir se ela deve ou não ir
para o espaço dedicado a consultas curtas.
E você pode configurar
quantos segundos considera curtos.
Portanto, essa é uma marcação que você
tem na aceleração de consultas curtas.
Portanto, lembre-se de que a aceleração de
consultas curtas
é uma alternativa ao gerenciamento de
carga de trabalho
do WLM se tudo o que você quiser
fazer é acelerar consultas curtas e
garantir que
elas não fiquem atrás de consultas mais
longas.
E ele pode funcionar com instruções CREATE
TABLE AS ou instruções SELECT somente
leitura.
Por fim, você precisa saber o que
o comando VACUUM faz com o Redshift.
VACUUM é o comando usado para
recuperar o espaço das linhas excluídas
e restaurar a ordem de classificação.
Basicamente, ele limpa sua mesa.
Há quatro tipos diferentes de comandos.
O primeiro é VACUUM FULL.
Essa é a operação padrão do VACUUM.
Ele recorpora todas as linhas e
recupera o espaço das linhas excluídas.
Há também o VACUUM DELETE ONLY, que é o
mesmo que um VACUUM completo, exceto pelo
fato
de que ele ignora a parte de
classificação.
Portanto, ele está apenas recuperando o
espaço da
linha excluída e não está realmente
tentando reordená-la.
Você também pode fazer um VACUUM SORT
ONLY, que
reordenará a tabela, mas não recuperará
espaço em disco.
E, por fim, há o VACUUM REINDEX,
que é usado para reinicializar índices
intercalados.
Lembre-se de que falamos sobre as
diferentes chaves de
classificação que você pode ter, sendo uma
delas intercalada.
Portanto, o REINDEX analisará novamente a
distribuição dos valores
nas colunas de chave de classificação da
tabela
e, depois disso, executará uma operação
VACUUM completa.
E, por fim, vamos falar sobre os
antipadrões do Redshift.
Isso também vem diretamente do white paper
do AWS Big Data sobre as
coisas para as quais eles não querem que
você use o Redshift.
Um deles é para conjuntos de dados
pequenos.
Portanto, lembre-se de que o ponto forte
do Redshift
é o fato de ser enorme e altamente
dimensionável.
Se você tiver apenas uma mesa pequena que
deseja armazenar,
o RDS pode ser uma opção melhor para isso.
OLTP, mais uma vez, eles não podem
enfatizar o suficiente
que o Redshift é feito para consultas
analíticas para OLAP.
Se você precisar fazer consultas
transacionais muito rápidas,
é melhor usar o RDS ou o DynamoDB.
E eles também estão listando dados não
estruturados
para mim, o que é um pouco estranho
porque o espectro do Redshift existe para
permitir
que você consulte dados não estruturados
no S3.
Mas se você precisar fazer algum ETL,
deverá fazê-lo primeiro com o EMR ou
o Glue ETL ou algo do gênero.
E não é adequado para armazenar dados
de blob, ou seja, arquivos binários
grandes.
Se você precisar armazenar arquivos
binários grandes em
seu data warehouse, é melhor armazenar
apenas
referências a esses arquivos onde eles
residem
no S3, e não os próprios arquivos.
Bem, isso é muito sobre o Redshift,
mas, novamente, você precisa se aprofundar
muito no Redshift para o exame.
Vale a pena entender e lembrar tudo
o que está escrito nesses slides.
