Agora que sabemos o que é um DNS,
vamos dar uma olhada no Amazon Route 53.
Portanto, esse é um DNS altamente disponível,
dimensionável, totalmente gerenciado e autoritativo.
O que significa autoritativo?
Isso significa que o cliente pode atualizar os registros de DNS,
Portanto, a ideia é que você tenha seus clientes e eles
queiram acessar sua instância EC2 @example. com, mas no momento sua
instância EC2 tem apenas um IP público.
Portanto, o que vai acontecer
é que vamos escrever alguns registros DNS no Amazon Route
53, em uma zona hospedada, e quando o cliente estiver solicitando
um exemplo. com, então o serviço Route
53 poderá dizer: "Ei, você está procurando
por este IP 54. 22. 33. 44" e, em seguida, os
clientes poderão se conectar diretamente
à nossa instância do EC2.
Assim, o Route 53 também é um registrador de domínios,
portanto, será possível registrar nossos próprios nomes de
domínios lá, por exemplo. com, e faremos isso
na prática para que possamos começar
a usar esse serviço.
Portanto, temos a capacidade de verificar também
a integridade dos recursos no Route
53. Veremos isso na seção.
E esse é o único serviço
no AWS que fornecerá SLA de 100% de disponibilidade.
Por fim, por que ela se chama Route 53?
Bem, 53 é uma referência à porta DNS tradicional
usada pelos serviços DNS, daí o nome.
Portanto, no Route 53, você definirá vários registros de
DNS e os registros definirão como você deseja rotear o tráfego
para um domínio específico.
Portanto, cada registro conterá muitas informações, como
o domínio ou os nomes de subdomínio, por exemplo.
O tipo de registro e veremos quais tipos de
com.
registro estão disponíveis, por exemplo, pode ser A ou AAAA.
Em seguida, o valor, ou seja, o valor do registro,
por exemplo, 12. 34. 56. 78 A política
de roteamento,
que é como o Route 53 responderá às consultas.
O TTL, que é o tempo durante o qual o
registro será armazenado em cache nos resolvedores de DNS, também
chamado de time to live.
Além disso, temos vários tipos diferentes de relatórios
de DNS compatíveis no Route 53.
Portanto, os que você deve conhecer são A, A quádruplo, CNAME
e NS, portanto, daremos uma olhada neles
na prática.
E os registros avançados que você pode definir,
mas que não precisamos saber do ponto de vista do exame,
são todos os que acabei de escrever aqui.
Então, vamos aprender sobre os tipos de registros importantes
que precisamos conhecer do ponto de vista de um exame.
Portanto, o registro A é muito simples,
serve para mapear um nome de host em um IP IPv4.
Portanto, é quando você tem, por exemplo, um exemplo. com que será direcionado
para 1. 2. 3. 4.
Ok, ótimo.
Então, temos o quádruplo A.
Portanto, a ideia é a mesma
de A, mas desta vez vamos combinar
o nome do host com um endereço IPv6.
Em seguida, temos um CNAME, que é usado para mapear
um nome de host para outro nome de host.
E o nome do host de destino, é claro, pode ser um registro
A ou um registro A quádruplo.
Não é possível criar CNAMES no Route 53 para
os nós superiores de um namespace DNS ou do Zone Apex,
e veremos isso em uma palestra futura para entender
como isso funciona.
Por exemplo, você não pode criar um CNAME para o exemplo. com, mas você pode criar um registro
CNAME para www. exemplo. com.
Portanto, veremos como podemos lidar com isso em uma palestra futura.
E, finalmente, NS é para servidores de nomes da zona hospedada.
Eles são os nomes de DNS ou endereços IP dos servidores que podem
responder às consultas de DNS para sua zona hospedada, e isso controlará
como o tráfego é roteado para um domínio.
Então, vamos dar uma olhada no que são zonas hospedadas.
Portanto, as zonas hospedadas são um contêiner de registros
e definirão como rotear o tráfego para
um domínio e seu subdomínio.
Portanto, temos dois tipos de
zona hospedada: as zonas públicas e as zonas hospedadas privadas.
Portanto, sempre que você compra um nome de domínio
público, por exemplo, mypublicdomain. com, esse é um nome de domínio público
e, portanto, podemos criar uma zona hospedada pública e essa zona
pública pode responder à consulta: "Ei, qual é o IP, o IP
subjacente do aplicativo de nome de domínio1.
também temos zonas privadas hospedadas.
mypublicdomainname. com? Mas
E esses são nomes de domínio que não
estão disponíveis publicamente, são privados,
e somente você, em sua própria nuvem privada virtual ou VPC, pode resolver
esse URL.
Por exemplo, application1. empresa. interno.
Se você trabalha em uma empresa
privada, talvez já tenha visto isso. Às vezes, eles
têm URLs que só podem ser acessados de dentro da rede corporativa,
porque esse é um URL privado, esse é um registro DNS privado
e, nos bastidores, há um registro DNS privado.
Portanto, para todas as zonas hospedadas que você criar no AWS, você
pagará 50 centavos de dólar por mês, o que
significa que o uso do Route 53 não é gratuito.
E se você for registrar um nome de domínio,
como farei na prática, isso
custará no mínimo US$ 12 por ano.
Portanto, só para que você saiba, esta seção não é gratuita.
Portanto, zonas hospedadas públicas versus privadas, só para entender.
Portanto, a zona hospedada pública pode ser respondida, pode
responder a consultas de clientes públicos.
Portanto, quando você usa um navegador
da Web, por exemplo, e diz: "Ei, me dê um exemplo. com" e, em seguida, retorna um IP.
E, na outra extremidade, temos a zona hospedada privada.
Portanto, é de dentro de sua VPC que eles vivem.
Assim, eles permitem que você identifique recursos
privados com nomes de domínio privados.
Assim, por exemplo, temos uma instância EC2 que queremos
identificar com webapp. exemplo. Internamente, temos
outra instância do EC2 que queremos identificar
com a API. exemplo. interno, e então temos um banco de dados
que queremos identificar com o banco de dados. exemplo. interno.
Nesse caso, registraremos uma zona hospedada privada e, em seguida,
caso a primeira instância do EC2 esteja solicitando
a API. exemplo. interno, então a zona
hospedada privada tem uma resposta para ele, que é o
IP 10 privado. 0. 0. 10.
Em seguida, a instância do EC2 se conectará
à segunda instância do EC2, que talvez precise
se conectar ao banco de dados.
Então, ele dirá: "Ei, o que é banco de dados. exemplo. interno? E a zona hospedada
privada dirá: "Bem,
este é este IP privado. Em seguida, a instância do EC2
pode se conectar diretamente
ao banco de dados.
Portanto, a zona hospedada pública e a zona hospedada
privada funcionam exatamente da mesma maneira, mas apenas a zona
hospedada pública permite que qualquer pessoa da Internet consulte
seus registros, portanto, isso é para seus registros
públicos, enquanto uma zona hospedada privada só é consultada de
dentro de seus recursos privados, por exemplo, sua VPC.
Agora vamos para a próxima
aula para registrar um domínio e criar alguns
registros.
Então, vejo você na próxima palestra.
