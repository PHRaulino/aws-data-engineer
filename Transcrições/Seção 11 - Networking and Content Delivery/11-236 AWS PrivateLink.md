Agora, vamos falar sobre o AWS PrivateLink,
também da família VPC Endpoint Services.
Então, como isso funciona?
Bem, digamos que você tenha um serviço que executa no AWS, ou que
haja um fornecedor no Marketplace, e ele executa
um serviço em sua própria conta em seu próprio
VPC.
E eles querem expor um serviço aos clientes da AWS.
Portanto, para milhares de VPCs, eles precisam ter acesso privado a esse serviço,
para estabelecer uma conectividade.
isso não é escalonável e não é muito seguro.
O que você deseja é usar outra
coisa, e essa outra coisa é um link privado.
Portanto, um link
privado permite que você conecte um serviço em execução na sua VPC
a outras VPCs de forma direta e privada.
Portanto, não requer peering de VPC ou gateway de Internet,
porque é da rede privada, ou NAT
ou tabelas de rotas ou algo do gênero.
Então, vamos examinar um diagrama.
Digamos, por exemplo, que você esteja conversando com
um fornecedor no AWS Marketplace e que ele execute um serviço de aplicativo.
Portanto, eles têm seu próprio serviço que você
deseja usar em seu próprio VPC.
E você quer ter acesso a ele a partir de sua própria VPC em
suas próprias contas com seus próprios aplicativos de consumo.
Nesse caso, você pedirá ao fornecedor que faça
um link privado.
No lado deles,
será necessário criar um balanceador de carga de rede
para expor esse serviço.
No seu lado, você
criará uma interface de rede elástica e, em seguida,
estabelecerá um link privado entre os dois para ter
acesso privado ao balanceador de carga
de rede e, portanto, ao
serviço deles.
Na verdade, todo o tráfego da Internet não passará pela
Internet pública, mas
sim pela sua rede privada.
Portanto, todas as comunicações permanecerão privadas.
Assim, para cada novo cliente que esse
terceiro precisar, tudo o que
ele terá de fazer é criar um novo link privado para seus
clientes, o que é muito fácil de gerenciar
e muito mais escalável.
Então é isso, espero que você tenha gostado desta
palestra e nos veremos na próxima palestra.
