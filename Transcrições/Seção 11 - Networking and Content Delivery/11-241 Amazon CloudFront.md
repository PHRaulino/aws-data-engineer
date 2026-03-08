Agora vamos falar sobre o
CloudFront. O CloudFront
é uma rede de distribuição de conteúdo ou
CDN.
Portanto, sempre que você vir CDN no
exame, pense no CloudFront.
Ele melhora o desempenho da leitura ao
armazenar em cache
o conteúdo do seu site em diferentes
locais de borda.
em todo o mundo, seus usuários em
todo o mundo terão uma latência menor,
o que melhorará a experiência do usuário.
O CloudFront é composto por centenas de
pontos de presença globalmente, incluindo
locais de
borda e caches em todo o mundo.
Além disso, por ter o conteúdo distribuído
globalmente, estamos obtendo proteção
contra DDoS.
Portanto, DDoS é um tipo de ataque em que
todos
os servidores do mundo são atacados ao
mesmo tempo.
Veremos isso mais adiante neste curso,
e a ideia é que o
CloudFront, como seu aplicativo é mundial,
esteja protegido contra esses ataques
também usando algo chamado Shield
e Web Application Firewall, que
veremos na seção de segurança.
Portanto, se você quiser dar uma olhada em
um
mapa do mundo, este é o mapa e vemos
alguns locais de borda, bem como caches de
borda.
Digamos que tenhamos criado um bucket S3 e
um site em nosso bucket S3 na Austrália,
mas tínhamos um usuário talvez nos Estados
Unidos.
Então, o que o usuário fará
é solicitar o conteúdo de um
local de borda americano usando o
CloudFront, e o CloudFront poderá
buscar o conteúdo na Austrália.
Agora, se outro usuário nos EUA
solicitar o mesmo conteúdo, ele
será servido diretamente da borda
e não irá até a
Austrália para servir esse conteúdo.
Da mesma forma, se um usuário estiver na
China,
ele se comunicará com um ponto de presença
chinês
e será redirecionado para os buckets do
S3, e
o conteúdo será armazenado em cache na
borda.
O CloudFront tem várias origens, que são
basicamente backends
aos quais você deseja que o CloudFront se
conecte.
Por exemplo, temos um bucket do Amazon S3.
Portanto, ele é usado para distribuir
arquivos
e armazená-los em cache na borda.
Ou para carregar arquivos diretamente no
Amazon
S3 por meio do Amazon CloudFront.
E o acesso entre o CloudFront e o
Amazon S3 é protegido usando algo chamado
controle de acesso à origem ou OAC.
Você também pode conectar o CloudFront a
qualquer coisa em sua VPC.
Portanto, ele é chamado de origem VPC
e destina-se a aplicativos hospedados em
sua
rede na Amazon, dentro das sub-redes
privadas.
Portanto, pode ser um balanceador de
aplicativos privado,
pode ser um balanceador de carga de rede
privada ou até mesmo instâncias privadas
do EC2.
Você também pode se conectar a uma origem
personalizada
por meio do protocolo HTTP, que pode ser,
por
exemplo, no site do S3; primeiro, você
deve habilitar
o bucket como um site estático do S3, ou
pode ser qualquer backend HTTP público que
você queira.
Por exemplo, se você tiver um balanceador
de
carga público, poderá conectá-lo
diretamente ao CloudFront.
Então, em um nível mais alto, como o
CloudFront funciona?
Temos a localização da borda em todo o
mundo, certo?
E, em seguida, ele se conectará à sua
origem.
Portanto, seria um bucket S3 ou um
servidor HTTP.
E quando o cliente se conectar e fizer uma
solicitação HTTP para o seu local de
borda, o
local de borda verá se ele está no cache.
Se não o tiver no cache, ele irá até
a origem para obter os resultados da
solicitação.
E, depois de recuperar os resultados, ele
os
armazenará em um cache local para que, se
outro cliente solicitar o mesmo conteúdo
do
mesmo local de borda, o local de
borda não precise ir até a origem.
Portanto, se tivermos o S3 como origem, se
olharmos
para a nuvem, o seu bucket do S3 será
a sua origem em alguma região e, em
seguida,
você terá locais de borda em todo o mundo,
por exemplo, em Los Angeles, e seus
usuários que
acessam o local de borda em Los Angeles
receberão o conteúdo diretamente pelo
local de borda.
Mas, primeiro, o local da borda o obterá
do
bucket S3 de origem por meio da rede
privada.
E o bucket S3 será protegido usando um
controle de acesso de origem e modificando
a
política do bucket S3 no bucket S3.
O mesmo acontece quando temos um usuário
em São Paulo, por exemplo, no Brasil.
Novamente, esse será outro local de borda,
que atenderá
aos usuários próximos ao Brasil e, em
seguida, será
uma conexão privada entre seu local de
borda
e seu bucket S3 e assim por diante.
Portanto, usando o CloudFront e os locais
de borda, podemos
ver que o conteúdo do nosso bucket S3 em
uma
região pode ser distribuído em todo o
mundo por
meio dos locais de borda ou pontos de
presença.
Portanto, uma pergunta comum é: qual é a
diferença entre o CloudFront e algo como a
replicação do S3? Bem, se você tiver o
CloudFront, estará usando a rede Global
Edge.
Portanto, trata-se de 216 pontos de
presença.
E os arquivos serão armazenados em cache
em
cada local de borda, talvez por um dia.
Portanto, isso é incrível se você
tiver conteúdo estático que precisa estar
disponível em qualquer lugar do mundo.
A replicação entre regiões do S3 é
diferente.
Ele deve ser configurado para cada região
em
que você deseja que a replicação ocorra.
Portanto, isso não se aplica a todas as
regiões do mundo.
E os arquivos serão atualizados quase em
tempo real,
de modo que não haverá armazenamento em
cache.
E é apenas para leitura.
Portanto, isso é ótimo se você tiver
conteúdo
dinâmico que precisa mudar o tempo todo e
estar disponível com baixa latência em
algumas regiões.
Portanto, esses objetivos são muito
diferentes.
O CloudFront é uma CDN, que armazena em
cache o
conteúdo em todo o mundo, enquanto a
replicação entre regiões
do S3 replica um bucket inteiro em outra
região.
Espero que isso faça sentido com relação
ao CloudFront.
Na próxima aula, veremos como podemos
configurar uma distribuição do CloudFront
nos
buckets do CloudFront e do S3.
Então, nos vemos na próxima palestra.
