Certo, então agora
vamos falar sobre como podemos estabelecer
a conectividade entre a VPC e outras estruturas.
Portanto, a primeira coisa é chamada de emparelhamento de VPC.
Então, digamos que você tenha duas nuvens privadas
virtuais, que estejam em duas contas diferentes
ou em duas regiões diferentes,
e você queira conectá-las como
se fizessem parte da mesma rede.
Portanto, queremos nos conectar
à VPC de forma privada usando a rede do AWS.
Isso fará com que elas se comportem
como se estivessem na mesma
rede, portanto, temos a VPC A e a VPC B e, se quisermos
uma conexão de peering de VPC de A para B.
Muito simples.
Para garantir que essas VPCs possam ser conectadas, você
precisa se certificar de que os intervalos
de IPs definidos para cada VPC não estejam sobrepostos.
Porque para poder endereçar a rede para outra VPC, você precisa
falar com um endereço IP.
Portanto, se obviamente os intervalos de rede se sobrepuserem,
a rede não saberá para onde ir.
Portanto, para se conectar à VPC, você precisa
se certificar de que o intervalo de endereços IP em que ela
opera seja diferente e não se sobreponha.
E uma conexão de emparelhamento VPC não é transitiva.
Portanto, ele deve ser estabelecido para cada
VPC que precisa se comunicar entre si.
O que quero dizer é que, se conectarmos a VPC
C por meio de uma conexão de peering de VPC entre A
e C, B e C não poderão se comunicar entre si.
Não há transitividade no emparelhamento VPC.
Isso significa que, se eu quiser estabelecer
conectividade entre a VPC B e a VPC C, precisarei
criar sua própria conexão de peering
de VPC entre B e C.
Isso é o que significa o emparelhamento de VPC.
Portanto, à medida que você adiciona
mais e mais VPCs, precisa adicionar mais e mais conexões de peering.
Ok, esse é o número um.
Número dois, endpoints de
VPC, que serão muito importantes nesse exame.
Portanto, os endpoints permitem que você
se conecte aos serviços da AWS usando uma rede privada
em vez de usar a rede pública da Internet.
Então, algo que talvez
você não saiba é que todos os serviços da AWS são públicos, certo?
Assim, sempre que suas instâncias do EC2, por exemplo,
usam os serviços da AWS, elas se comunicam publicamente com a AWS, mas, às vezes,
suas instâncias do EC2 não estão conectadas
às sub-redes públicas e, portanto, você deseja que
elas acessem, de forma privada, seus
serviços da AWS.
Portanto, esse é o ponto de extremidade da VPC.
Portanto, isso só lhe dá segurança e
menor latência para acessar os serviços da AWS.
Então, vamos dar um exemplo.
Temos uma sub-rede privada e uma instância
do EC2 nela, e ela deseja acessar o Amazon S3 e o DynamoDB,
que estão fora da VPC, no domínio público.
Em seguida, podemos criar um gateway de endpoint
VPC, e isso é apenas para S3 e DynamoDB, portanto, gateway
de endpoint, e veremos o que são S3 e DynamoDB neste curso,
obviamente.
Portanto, sua instância do EC2 se comunica com esse endpoint de
VPC e tem acesso ao S3 e ao DynamoDB de forma privada.
Como você pode ver,
o tráfego não passa pela Internet.
E, em seguida, para a interface de ponto de extremidade
VPC, esse é o restante do serviço
e só é usado em sua VPC, o que significa que
podemos criar, por exemplo, uma interface de ponto
de extremidade VPC em sua sub-rede privada e, por meio dessa
interface de pontos de extremidade, por meio dessa ENI,
temos acesso privado ao CloudWatch.
Portanto, os endpoints de VPC são muito, muito
úteis sempre que você precisar de acesso privado de dentro da sua VPC
a um serviço da AWS, certo?
É disso que você precisa se lembrar.
Os outros exames precisam saber a diferença entre
gateway e interface.
Não acredito que você
precise saber isso para o exame
de desenvolvedor certificado, mas saiba que sempre que o exame
pedir que você se conecte de forma privada a um serviço da AWS,
um endpoint de VPC será o caminho.
Então, como estabelecemos a conectividade entre o
data center local, que pode
ser o prédio do seu escritório, por
exemplo, e a VPC na nuvem?
Portanto, a primeira maneira é chamada de VPN
site a site, para conectar um dispositivo VPN local ao AWS.
A conexão será automaticamente criptografada
e passará pela Internet pública.
Portanto, neste exemplo, estabelecemos uma
VPN, rede virtual privada,
entre seu data center local e sua VPC, que
passa pela Internet pública.
Isso é muito fácil de configurar e muito rápido.
Você pode fazer a configuração em questão de minutos.
E pronto, você tem uma conexão privada,
ou uma conexão criptografada,
desculpe, pela Internet pública com a sua VPC.
A outra opção é a conexão direta.
Ele atinge o mesmo objetivo,
ou seja, estabelecer uma
conexão entre seu data center local
e sua VPC, mas desta vez é uma conexão física.
Isso significa que a conexão será privada,
não passará pela Internet pública,
será segura e rápida, e passará pela rede
privada.
E como se trata de uma linha privada para sua VPC, leva pelo menos
um mês para ser estabelecida, pois
é necessário algum trabalho para
ter uma conectividade privada com a AWS.
Portanto, isso é chamado de conexão
direta, e essa é a rota privada.
Como podemos ver, tanto a VPN quanto a conexão direta
atingem o mesmo objetivo,
mas com assuntos diferentes e cronogramas diferentes.
Pronto, isso é tudo para a conectividade de sua VPC em
termos de peering de VPC externa, endpoints de VPC, VPN
site a site e conexão direta.
Espero que tenha sido útil
e nos veremos na próxima palestra.
