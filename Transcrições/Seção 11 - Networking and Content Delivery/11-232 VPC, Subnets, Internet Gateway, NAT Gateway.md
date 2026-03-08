primeiro vamos fazer uma introdução à VPC e às sub-redes.
Portanto, VPC é uma nuvem privada virtual,
o que significa que é uma
rede privada dentro da nuvem da AWS que permite que
você implemente seus recursos nela.
E um VPC é um recurso regional.
Portanto, se você tiver duas regiões do AWS,
elas terão dois VPCs diferentes.
Portanto, uma VPC é representada desta forma.
Dentro de sua VPC, que é apenas uma construção lógica, você
tem sub-redes.
E as sub-redes permitem que você divida
sua rede dentro da VPC, e as sub-redes
são definidas no nível da zona de disponibilidade.
Portanto, temos um AZ, ou seja, AZ A, neste exemplo.
E podemos ter várias sub-redes.
Portanto, a primeira sub-rede que vou criar é uma sub-rede pública.
Como você pode ver, a sub-rede pública é uma sub-rede
que pode ser acessada pela Internet.
Assim, essa sub-rede pode acessar a rede mundial de computadores
e também pode ser acessada a partir da rede mundial de computadores.
Então, temos outro tipo de sub-rede, chamada
de sub-rede privada.
E uma sub-rede privada é uma sub-rede
que não pode ser acessada pela Internet, certo?
E como podemos definir isso?
Veremos isso no próximo slide.
Portanto, para definir o acesso à Internet e entre sub-redes, usaremos
tabelas de rotas.
Portanto, em sua VPC, você definirá
várias tabelas de rotas, que
definirão como a rede flui entre todas
as diferentes sub-redes.
Lembre-se de que tudo
é de alto nível nesta seção, portanto, não faremos nada prático,
mas tente se lembrar desse
conceito.
Você verá que, em breve, isso fará sentido para você.
Portanto, temos uma instância do EC2 em
uma sub-rede pública, que tem acesso
à Internet, e temos uma instância do EC2 em uma sub-rede privada,
que não tem acesso à Internet, ou a Internet
não tem acesso a ela.
O motivo é que queremos que ele seja mais
seguro, mais privado, certo?
Portanto, se observarmos um diagrama maior para
a VPC, teremos nossa infraestrutura de nuvem e uma região.
Dentro da região, temos um VPC.
E a VPC tem um conjunto de intervalos de IP.
Por isso, ele é chamado de intervalo CIDR.
E esse é apenas um intervalo de IP permitido em sua VPC.
E temos dois AZ neste exemplo.
Portanto, no primeiro AZ, terei
uma sub-rede pública e uma sub-rede privada.
E podemos iniciar nossas instâncias do EC2 em cada sub-rede que desejarmos.
E no AZ dois, temos uma sub-rede
pública e uma sub-rede privada.
Portanto, essa é a aparência da VPC em um nível alto,
e isso é muito comum.
Na VPC que é criada para você quando
usa sua nuvem no AWS, você só tem
sub-redes públicas.
Você não tem sub-redes privadas.
Mas você tem uma sub-rede pública por AZ.
E você tem uma VPC em cada uma das regiões
criadas para você.
Ele é chamado de VPC padrão.
Ok, a seguir, em sua rede, falamos
sobre sub-rede pública e sub-rede privada,
mas vamos nos aprofundar um pouco
mais e falar sobre gateways de Internet e gateways NAT.
Portanto, se voltarmos ao mesmo diagrama, digamos
que temos uma instância do EC2 em uma sub-rede pública.
O que torna a sub-rede realmente pública?
Como ele pode acessar a Internet?
Bem, para isso, usamos um gateway de Internet.
Nosso gateway de Internet ajudará nossas instâncias de VPC
em nossas sub-redes a se conectarem à Internet.
Portanto, aqui está seu gateway de Internet. Ele reside em sua VPC.
Assim, a sub-rede pública terá uma
rota para o gateway da Internet.
Portanto, sua sub-rede pública, por exemplo,
sua instância do EC2 nessa sub-rede pública tem uma
rota para seu gateway de Internet.
E seu gateway de Internet sabe como se comunicar com a Internet.
E é isso que torna uma sub-rede uma sub-rede pública.
Portanto, uma sub-rede pública terá uma rota,
uma rota direta para um gateway da Internet.
Então, agora vamos dar outro exemplo.
Temos nossa instância EC2 na sub-rede privada.
E queremos que ele também seja capaz de acessar a Internet,
por exemplo, para obter atualizações de software.
Mas não queremos que ele seja acessível pela Internet.
Não queremos que a Internet possa
acessar esses sites em nossa sub-rede privada, por exemplo.
Portanto, para
isso, usamos o que chamamos de gateway NAT ou instância NAT.
Eles fazem a mesma coisa.
Eles fornecem NAT para suas sub-redes privadas, mas
os gateways NAT são gerenciados pela AWS.
Portanto, você não precisa se preocupar
em provisioná-los e escaloná-los,
enquanto as instâncias NAT são autogerenciadas e ambas
permitem que as instâncias em suas sub-redes privadas acessem
a Internet e permaneçam privadas.
Então, como isso funciona?
Vamos implantar um gateway NAT ou uma instância NAT
em nossa sub-rede pública
e, em seguida, criaremos
uma rota da sub-rede privada para a instância ou gateway NAT.
E o NAT tem uma rota para o gateway da Internet porque está
na sub-rede pública e, portanto,
sua sub-rede privada pode acessar através
do NAT todo o caminho até a Internet.
E esse é o objetivo dos gateways NAT.
Portanto, essa é uma infraestrutura típica do AWS.
E os gateways NAT, instâncias NAT, entrarão
em ação mais tarde neste curso, quando
falarmos sobre funções lambda, certo?
Mas tente se lembrar disso. Este é um diagrama muito simples.
E fique à vontade para revisitar esta seção mais adiante
neste curso.
Talvez isso faça muito mais sentido,
mas mesmo assim eu queria apresentar os conceitos a você.
Então, vejo você na próxima palestra para conhecer mais conceitos de VPC.
