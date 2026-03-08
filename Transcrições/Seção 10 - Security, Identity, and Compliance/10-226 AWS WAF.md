o AWS WAF, o Web Application Firewall.
Ele é usado para proteger seu aplicativo da Web
contra explorações comuns da Web na Camada 7.
Apenas para lembrar, a Camada 7 é HTTP, portanto,
protege você contra explorações de HTTP.
Em comparação, a Camada 4 é para o protocolo TCP ou UDP.
Portanto, esse WAF, esse Web Application Firewall, pode
ser implementado no balanceador de aplicativos e no gateway de API, no CloudFront,
na API GraphQL do AppSync ou nos pools de usuários do Cognito.
Portanto, lembre-se de que isso é muito importante.
Lembre-se dos alvos do WAF
porque o exame tentará enganá-lo
e, por exemplo, fará com que você implemente o WAF em um NLB,
mas isso não é possível.
Assim, depois de implementar um firewall nesses serviços, você pode
definir ACLs da Web, que são listas
de controle de acesso à Web, e suas regras.
Assim, você pode definir uma regra, por
exemplo, para filtrar com base em endereços IP.
Assim, você pode definir um conjunto de IPs.
Cada conjunto de IPs pode ter até 10.000 endereços IP.
E se você precisar de mais endereços IP, poderá
usar várias regras para mais IPs.
Você também pode filtrar com base em cabeçalhos HTTP, corpo.
Você pode usar strings de URI para se proteger
dos ataques mais comuns, como injeção de
SQL e script entre sites.
Você pode ter restrições de tamanho para garantir
que a solicitação tenha apenas até, por exemplo, dois megabytes ou correspondência
geográfica para permitir ou bloquear países específicos.
E você pode até ter regras baseadas em taxas para
contar as ocorrências de solicitações por IP para proteção
contra DDoS, por exemplo, para impedir que um IP específico
envie mais de 10 solicitações por segundo.
Portanto, essas ACLs da Web são regionais, exceto no caso do CloudFront,
em que são definidas globalmente.
E se você vir o termo grupo de regras, bem, é um conjunto,
é um conjunto razoável de regras que você pode
adicionar a muitas ACLs da Web.
Portanto, isso serve apenas para organizá-los.
Portanto, o WAF tem um caso de uso muito bom.
E se quisermos obter um IP fixo em nosso aplicativo ao usar
o WAF com um balanceador de carga de aplicativos?
Portanto, o WAF não é compatível com o Network
Load Balancer porque o NLB opera na Camada 4 e o WAF é para a Camada 7.
Portanto, para fornecer WAF, você precisa ter um balanceador
de carga de aplicativos.
Mas sabemos que um balanceador de aplicativos
não tem IPs fixos.
Portanto, para resolver um problema, podemos usar um
Global Accelerator para obter um IP fixo
para o aplicativo e, em seguida, ativar o WAF em nosso ALB.
Portanto, a arquitetura é parecida com a seguinte.
Temos uma região com um ALB e instâncias do EC2.
Vamos colocar nosso ALB na frente de um Global Accelerator
para obter um IP fixo para nosso aplicativo.
E vamos anexar um Web Application Firewall
com uma WebACL na mesma região em que está localizado
o nosso balanceador de aplicativos.
Portanto, atingimos nossa arquitetura-alvo.
Então é isso para esta palestra.
Espero que você tenha gostado.
E eu o verei na próxima palestra.
