Então, como podemos conectar o CloudFront
ou a uma instância do EC2 como origem?
Portanto, temos duas maneiras, e esta é a melhor
maneira e a mais nova.
Isso é chamado de uso de origens VPC.
E permite que você forneça conteúdo diretamente
de aplicativos hospedados
em suas sub-redes privadas na VPC.
E tudo pode permanecer privado.
Você não precisa expor nada disso na Internet.
Isso significa que podemos fornecer tráfego
para balanceadores de aplicativos privados,
balanceadores de carga de rede e instâncias do EC2.
Então, como isso funciona?
Bem, vamos criar uma distribuição do CloudFront, que
tem vários locais de borda, e nossos usuários acessarão
o CloudFront dessa forma.
Mas, a partir do CloudFront, criaremos uma origem
VPC e conectaremos essa origem VPC ao nosso backend.
Portanto, pode ser, novamente, um ALB, um NLB ou uma instância do EC2.
E, em seguida, o CloudFront fará o link por meio da origem
da VPC para direcionar o tráfego para suas sub-redes e aplicativos privados.
E, do ponto de vista da rede, essa é uma das formas
mais seguras de fazer a configuração porque, bem, seus
aplicativos ainda são hospedados de forma privada,
internamente, e você escolhe o que expor
por meio do CloudFront, o que é muito útil.
Se você quisesse usar uma rede pública,
esse era o método anterior
à existência do recurso de origem VPC.
E ainda quero mostrá-lo
a você porque é bom entender o que foi feito antes.
Você precisava ter uma instância do EC2 que fosse pública.
Portanto, você tinha uma lista de locais de borda com
seus IPs públicos.
Use esse link para encontrar a lista
de todos os IPs do CloudFront
e certifique-se de alterar o grupo de segurança
para permitir que todos esses IPs públicos do local
de borda entrem em sua instância do EC2.
Portanto, ele seria
público, mas restrito apenas aos locais de borda.
E o mesmo vale para o caso de você
ter um balanceador de carga de aplicativos,
novamente, ele deveria ser público, mas suas
instâncias EC2 poderiam ser privadas.
E, em seguida, basta ter uma rede privada entre o
ALB e as instâncias do EC2 por meio do uso do grupo de segurança.
E, novamente, você deve se certificar
de que seu ALB tenha um grupo de segurança que
permita todos os IPs públicos provenientes do CloudFront.
Portanto, é um pouco mais tedioso
porque, em primeiro lugar, você precisa encontrar esses IPs públicos e
alterar o grupo de segurança.
Além disso, há o risco de que, se alguém
alterar o grupo de segurança de seu ALB ou de sua instância do EC2,
sua instância se torne pública para mais do que apenas
sua distribuição do CloudFront.
Mas essa era a maneira antiga.
Agora, a nova e melhor maneira é usar, é claro, as origens VPC.
Muito bem, então é isso nesta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
