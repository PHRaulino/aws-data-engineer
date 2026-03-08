Certo, então, antes de falarmos
sobre o Route 53, temos que falar sobre o que é um DNS?
Portanto, esta é uma palestra de nível básico, mas pelo menos
ajudará você a entender como o DNS funciona.
E isso é algo que você tem usado
nos bastidores todos os dias,
mas não sabe exatamente o que é.
Então, vamos dar uma olhada.
Portanto, um DNS é um sistema de nomes de domínio,
e o que ele fará é traduzir nomes de host amigáveis
para os endereços IP do servidor de destino.
Por exemplo, quando você digita em seu navegador
da Web, www. google. com, ele retornará
da Web poderá acessar nos
bastidores e obter alguns dados do Google.
Portanto, o DNS é a espinha dorsal da Internet.
É uma maneira de você entender
como traduzir esses URLs, esses nomes de host em IPs.
Portanto, há uma estrutura hierárquica de nomes para
o DNS e a ideia é que, na raiz
do www. google. com, por exemplo, há o . com, mas há
um exemplo. com, que é um pouco mais preciso.
Em seguida, www. exemplo. com ou api. exemplo. com.
Portanto, tudo isso será a hierarquia de seus nomes
de domínio.
Em seguida, precisamos definir
um pouco da terminologia relacionada ao seu DNS.
Portanto, há um registrador de domínios.
É aqui que você registrará seus nomes de
domínio, podendo ser o Amazon Route 53, o GoDaddy ou qualquer outro
registrador de domínios que possa encontrar on-line.
Em seguida, há os registros DNS, que têm tipos diferentes
e que serão examinados em detalhes nesta seção.
Portanto, pode ser A, AAAA, CNAME, NS, etc., etc.
Não se preocupe, veremos isso em detalhes nesta seção.
Um arquivo de zona que contém todos os registros de DNS.
Portanto, é assim que se faz a correspondência
entre esses nomes de host e IPs ou endereços.
Servidores de nomes são servidores
que de fato resolverão as consultas de DNS.
E vamos dar uma olhada nelas também nesta seção.
Os domínios de nível superior, que são . com, . nós, . em, . gov, . org, etc.,
etc.
Domínio de segundo nível que é a amazon. com e google. com.
Portanto, você pode ver que há duas palavras entre um ponto.
Portanto, se dermos uma olhada,
por exemplo, nesse FQDN, ou seja, no nome de domínio totalmente qualificado,
temos http://api. www. exemplo. com.
Está bem?
Portanto, o último ponto no final é chamado
de raiz e é a raiz de todos os nomes de domínio.
Em seguida, o . com,
portanto . com é seu TLD, ou seja, seu domínio de nível superior.
O exemplo. com será seu domínio de segundo nível.
Então temos o www. exemplo. com.
Esse é o seu subdomínio.
api. www. exemplo. com é seu FQDN, seu nome
de domínio totalmente qualificado.
O HTTP será seu protocolo e todas
essas coisas juntas serão seu URL.
Então, agora que conhecemos um pouco da terminologia,
vamos dar uma olhada em como o DNS funciona.
Portanto, temos um servidor da Web e digamos, por exemplo,
que temos um IP, um IP público, que pode ser
uma instância do EC2, por exemplo.
E o IP público é 9. 10. 11. 12 e queremos
poder acessá-lo usando
o exemplo. com.
Então, vamos registrar este exemplo. com em um de nossos
servidores para o DNS.
Mas vamos ver como o computador, seu navegador
da Web, pode acessá-lo e obter essa resposta.
Portanto, seu navegador da Web desejará acessar o exemplo. com.
E, para isso, ele solicitará o servidor DNS local.
"Ei, você sabe que exemplo. com é? Agora, esse servidor DNS
local geralmente é atribuído e gerenciado
por sua empresa ou atribuído dinamicamente
pelo seu provedor de serviços de Internet.
E se o servidor DNS local nunca tiver visto essa consulta antes,
o que ele fará é primeiro perguntar ao servidor DNS raiz
gerenciado pela I-C-A-N-N, a organização ICANN, e dirá: "Ei, você sabe
qual é o exemplo. com? Que é o primeiro servidor
que será perguntado.
E o servidor DNS raiz dirá: "Nunca
vi isso, mas sei que . com. Portanto,
. com é NS, portanto é um servidor de nomes
de registro NS e vai ver 1234 esse IP público.
Portanto, isso está dizendo
ao DNS local: "Ei, eu não tenho essa
resposta, mas estou aproximando você um pouco mais da resposta
porque conheço o . com, e
o domínio . com tem esse IP, 1234. Portanto, o servidor DNS
local diz: "Ok, ótimo.
Agora vou perguntar qual é o domínio de nível superior. Portanto,
o . com em 1234.
"Vou pedir a resposta de minha pergunta. Portanto, esse é outro domínio gerenciado
pela I-A-N-A, a IANA e o exemplo.
ok, será solicitado novamente a esse servidor DNS.
com,
Então, você conhece o exemplo. com?
E o servidor DNS dirá: "Ei, eu
sei sobre o exemplo. com.
Não tenho a resposta para sua pergunta imediatamente.
Não sei qual é o registro, mas
há um servidor chamado example. com que eu conheço, que
está em 5. 6. 7. 8, esse é um IP público
para o qual você deve perguntar a resposta à sua pergunta.
Assim, o servidor DNS local vai para o nosso servidor final,
que é o servidor DNS de domínio de segundo nível, um servidor
que será gerenciado pelo seu registrador
de domínios.
Portanto, poderia ser, por exemplo, o Amazon Route 53 e assim por diante.
Portanto, o servidor DNS dirá:
"Ei, você conhece o example. com? E o servidor DNS terá uma
entrada, por exemplo. com.
E assim ele dirá: "Ei, sim,
é claro que conheço o exemplo. com. E acontece que esse
exemplo. com, sei que
é um registro A e que o resultado
dele é o IP 9. 10. 11. 12.
Portanto, o servidor DNS agora sabe a resposta
perguntando recursivamente aos servidores DNS
e encontrando o mais específico.
E então ele diz: "Ok, ei, sim.
Vou colocar essa resposta no cache imediatamente porque quero
poder, se alguém me perguntar novamente,
por exemplo. com Eu quero saber
imediatamente, dê a eles a resposta. Assim, ele enviará de volta a resposta
para o navegador, e o navegador da Web agora tem
a resposta e, usando
esse endereço IP, poderá
acessar o servidor da Web.
Portanto, é assim que o DNS funciona.
Então, você tem usado o DNS nos bastidores durante
toda a sua vida.
Por exemplo, quando você acessa www. google. com que estiver
usando o DNS ou qualquer site.
Mas agora vamos ver como funcionam as consultas de DNS.
Portanto, esse é apenas um conhecimento
básico, pois agora vamos entrar no Route 53 e aprender
a gerenciar um servidor DNS por conta própria.
Espero que tenham gostado
e nos veremos na próxima palestra.
