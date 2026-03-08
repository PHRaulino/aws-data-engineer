Agora que já vimos todos
os aspectos da definição da rede em nossa VPC,
vamos falar sobre a segurança da rede.
Então, vamos falar sobre
o conceito de ACL de rede e grupos de segurança.
Portanto, estamos de volta à nossa VPC.
Ele tem uma sub-rede pública e uma instância do EC2.
Podemos criar uma NACL ou ACL de rede.
Que é um firewall que controla o tráfego
de e para as sub-redes.
E isso pode ter regras de permissão e negação.
Portanto, podemos permitir ou negar o tráfego.
E isso é explícito.
Você anexa essas NACLs no nível da sub-rede e
as regras incluem apenas endereços IP.
Portanto, você está dizendo que todo
o tráfego proveniente desse endereço IP é permitido, ou que todo o tráfego proveniente
desses endereços IP é negado, e assim por diante.
Portanto, a NACL está aqui e é o primeiro mecanismo de defesa de nossas sub-redes
públicas, e está no nível da sub-rede.
Portanto, como podemos ver, o tráfego
de entrada e saída da Internet passará primeiro
pela ACL da rede.
Mas ele ainda não chegou à nossa instância EC2.
Em seguida, temos os grupos de segurança,
que já foram vistos neste curso.
Portanto, os grupos de segurança são um firewall que
controla o tráfego de e para uma ENI, ou seja, uma interface de rede elástica
ou uma instância do EC2.
Como vimos, os grupos de segurança só podem
ter as regras de permissão e podem fazer referência
a endereços IP ou a outros grupos de segurança.
E isso é algo que já vimos neste curso.
Assim, anexamos um grupo de segurança à nossa instância
do EC2 e agora o tráfego pode fluir até
a nossa instância do EC2.
E temos o segundo mecanismo de defesa.
Portanto, vimos os grupos de segurança em profundidade neste curso, mas não tocamos
realmente nos NACLs.
Por quê? Porque quando você tem
uma VPC padrão, a NACL padrão permite
que tudo entre e saia.
E é por isso que não tivemos que alterar a ACL da rede neste curso
e também não faremos nenhum trabalho prático com ela.
Mas saiba que, antes que o tráfego da Internet
chegue à sua instância do EC2, ele precisa
passar por essa ACL de rede, que funciona
como um firewall.
Portanto, eles são muito diferentes da
rede SCL e do Grupo de Segurança.
E há uma tabela que resume isso.
Você não precisa se lembrar disso.
Isso é mais para o Solutions
Architect Associate ou o Sysap's
Associate certificado.
Mas a ideia é que o grupo de segurança seja anexado a uma
instância ou a uma ENI,
enquanto a ACL de rede está no nível da sub-rede.
O Grupo de segurança é composto apenas por regras de permissão,
enquanto que para a ACL de rede são regras de permissão e negação.
É stateful, o que significa que qualquer tráfego que chegue e retorne
é automaticamente permitido, independentemente de quaisquer
funções.
Já no caso da ACL de rede,
você precisa permitir a entrada e a saída do tráfego.
E aqui você pode ver o restante, mas isso é
bastante irrelevante para a certificação.
Ok, isso é só para você ficar curioso.
Então, agora que temos todo esse tráfego
fluindo pela nossa VPC, pela ACL de rede e pelos grupos
de segurança, estamos curiosos para saber se podemos
obter informações sobre todo esse tráfego
que passa por ela.
Podemos obter um registro dele?
E isso é chamado de registro de fluxo de VPC.
Portanto, isso capturará informações
sobre todo o tráfego IP que entra em suas interfaces.
Isso inclui os logs de fluxo da VPC, os logs de fluxo da sub-rede
e os logs de fluxo da ENI
ou da Elastic Network Interface.
Portanto, sempre que houver uma rede passando pela sua VPC, ela
será registrada em um log de fluxo.
E isso serve para ajudá-lo a monitorar e solucionar
problemas de conectividade.
Por exemplo, se quiser saber por que sua sub-rede não consegue
acessar a Internet ou por que uma sub-rede pode falar ou não pode
falar com outras sub-redes ou com a Internet para a sub-rede,
etc., etc.
Portanto, sempre que você tiver um problema de rede e precisar solucioná-lo,
é necessário examinar os logs de fluxo da
VPC, pois eles fornecerão tudo.
Todas as informações sobre o tráfego
permitido e negado.
Ele também capturará informações de rede de qualquer
coisa que seja gerenciada pela AWS.
Portanto, os Elastic Load Balancers, o ElastiCache, o RDS, o Aurora, tudo isso aparecerá
nos registros de fluxo da VPC.
E os dados dos registros de fluxo
da VPC podem ser enviados para
o Amazon S3, para o CloudWatch Logs e para o Kinesis
Data Firehose, de modo que você pode enviá-los
para vários locais no AWS.
Então é isso para esta palestra.
Espero que você tenha gostado.
Já vimos NACLs, grupos de segurança
e registros de fluxo de VPCs e nos vemos na próxima palestra.
