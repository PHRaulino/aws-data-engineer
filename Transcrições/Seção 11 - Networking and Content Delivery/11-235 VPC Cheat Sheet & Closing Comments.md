e sem nenhum hands-on, então
isso pode ter sido confuso.
Mas, na verdade, não quero sobrecarregá-lo com informações
práticas, pois isso não é para desenvolvedores certificados.
Você só precisa se lembrar de alguns conceitos
de toda essa seção.
Portanto, vou resumir tudo em um único slide e, acredite,
você estará preparado
para todas as perguntas sobre VPC durante o exame.
Portanto, não se estresse.
A primeira é a VPC, que significa
Virtual Private Cloud (nuvem privada
virtual), e usamos a VPC padrão durante todo o curso quando criamos
nossas instâncias do EC2.
Haverá um VPC padrão por região
da AWS que estamos usando.
As sub-redes estão vinculadas a zonas de disponibilidade específicas, e é
aqui que lançamos nossas instâncias do EC2.
E eles representam uma partição de rede de sua VPC.
O gateway de Internet é o que dá acesso às nossas
instâncias em nossas sub-redes públicas à Internet,
certo?
E eles são definidos no nível da VPC.
Os gateways NAT e as instâncias NAT darão acesso à Internet, desta
vez às nossas sub-redes privadas.
Portanto, nossas instâncias EC2 e sub-redes privadas.
As NACLs, Network ACL, são stateless, regras de sub-rede,
firewalls para entrada e saída, enquanto
os grupos de segurança,
que já vimos antes, são
stateful, operam no nível da instância do EC2 ou da ENI e podem fazer referência
a outros grupos de segurança.
Para o peering de VPC, isso nos permite conectar duas VPCs, desde que elas
não estejam sobrepostas.
E esse não é um emparelhamento de VPC transitivo.
Portanto, você precisa estabelecer conexões de
peering de VPC entre todas
as suas VPCs se quiser conectá-las umas às outras.
O VPC Endpoints fornecerá acesso privado aos serviços
da AWS dentro do seu VPC, e isso é algo que
veremos em palestras futuras para alguns serviços.
E o VPC Flow Logs fornecerá o registro do tráfego de
rede para garantir que você possa depurar se algo tiver acesso negado,
se o tráfego estiver bloqueado ou permitido na VPC.
Por fim, para estabelecer
a conexão do seu data center local com o AWS, você
tem a VPN Site a Site, que consiste
em ter uma conexão VPN pela Internet pública.
E o Direct Connect, se for
o caso, você deseja uma conexão privada direta com o AWS.
Portanto, não se preocupe se não tiver entendido tudo o que está escrito nessa
seção, pois você poderá voltar a ela mais tarde.
Como eu disse, no curso,
destacarei todos os recursos específicos de VPC de que precisamos e,
se você quiser, voltarei ao assunto no final, mas não
se estresse.
Estou falando muito, muito sério sobre isso.
Eu só queria lhe dar um pouco mais de informações
do que você precisava, só para ter certeza de que estamos na
mesma página e vamos embora.
Vamos seguir o caminho deste curso.
Confie em mim, ele se tornará muito mais desenvolvedor
muito, muito em breve.
Muito bem, é isso.
Eu o verei na próxima palestra.
