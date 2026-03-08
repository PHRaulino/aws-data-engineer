Portanto, ele é um dispositivo altamente
seguro e portátil
que permite coletar e processar dados na
borda e
migrar dados para dentro e para fora do
AWS.
Portanto, se você tiver uma migração de,
digamos, petabytes de
dados, o Snowball pode ser um bom caso de
uso.
Portanto, temos dois tipos de dispositivos
de borda Snowball.
Um é chamado de Edge Storage Optimized
(otimizado para armazenamento de borda) e
o outro é chamado de Edge Compute
Optimized (otimizado para computação de
borda).
E a diferença está em seu armazenamento.
Como você pode ver, um tem 210
terabytes e o outro tem 28 terabytes.
Então, obviamente, um é para armazenamento
e o
outro é usado apenas para o computador.
Então, deixe-me falar sobre as migrações
de dados.
Portanto, leva muito tempo para transferir
alguns dados
em uma velocidade de largura de banda
específica.
Por exemplo, se você quiser transferir cem
terabytes em uma conexão de um
gigabyte por segundo, levará 12 dias.
Portanto, quando você tem uma conexão
lenta, pode
ter conectividade limitada, largura de
banda limitada, custo
de rede muito alto e precisa compartilhar
a
largura de banda, por exemplo, com alguns
outros
aplicativos, a conexão pode não ser
estável.
Portanto, sempre que você tiver esse tipo
de
desafio, ou se levar, por exemplo, mais de
uma semana para transferir dados pela
rede,
a recomendação é usar um dispositivo
Snowball.
Portanto, a ideia é que, se você fizer o
upload diretamente para o
Amazon S3, é simples, mas pode usar toda a
sua largura de banda.
E se você usar o Snowball,
bem, receberá um dispositivo Snowball
físico,
você mesmo, em sua própria infraestrutura.
Portanto, é uma máquina física e, em
seguida, você
a carrega com os dados de que precisa
e, por fim, envia-a de volta ao AWS.
Em seguida, você terá um processo de
exportação
no AWS para levar seus dados do Snowball
para, por exemplo, um bucket do Amazon S3.
Portanto, esse é o principal caso de uso
de um dispositivo Snowball.
O outro é um caso de uso de computação de
borda.
Portanto, a ideia é que você queira
processar os dados
enquanto eles estão sendo criados em um
local de borda.
Por exemplo, é um caminhão na estrada, um
navio
no mar ou uma estação de mineração no
solo.
E esses locais podem não ter acesso à
Internet ou
ter acesso limitado à Internet ou à
capacidade de computação.
Então, aqui novamente, pedimos um desses
grandes dispositivos
de borda Snowball e fazemos computação de
borda.
Isso significa que temos o Compute
Optimized,
que é dedicado a esse caso de
uso para dispositivos otimizados para
pesquisa.
E, como eles têm capacidade de
computação, podemos executar instâncias do
EC2
ou funções Lambda diretamente nesses
dispositivos.
A ideia é que, depois que os dados
forem criados e processados, poderemos
enviá-los novamente para
o AWS, mas, usando um dispositivo de
computação de borda, poderemos
pré-processar os dados
ou fazer aprendizado de máquina na borda
ou transcodificar diretamente a mídia na
borda.
E esse é o caso de uso da computação de
borda.
Espero que isso faça sentido.
O serviço Snowball é realmente apenas algo
usado
para migrações de dados e computação de
borda.
Muito bem, é isso, espero que tenham
gostado e vejo vocês na próxima palestra.
