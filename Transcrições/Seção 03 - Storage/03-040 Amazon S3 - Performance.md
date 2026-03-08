Portanto, por padrão, o Amazon S3 é dimensionado automaticamente
para um número muito, muito alto de solicitações
e tem um S3 muito, muito baixo, entre 100 e 200 milissegundos para obter
o primeiro byte do S3.
Portanto, isso é bastante rápido.
E em termos de quantas solicitações por segundo
você pode obter, você pode obter 3.500 solicitações
PUT/COPY/POST/DELETE, por segundo,
por prefixo, e 5.500 solicitações GET/HEAD por segundo por
prefixo nos buckets.
Portanto, isso é algo que você pode obter
no site e acho que não está muito
claro, então vou explicar a você o que significa por segundo por prefixo.
Mas o que isso significa
em termos virais é que o desempenho é muito, muito
alto e não há limites para o número de prefixos em seu bucket.
Então, vamos pegar um exemplo de quatro objetos chamados
file e analisar o prefixo desse objeto.
O primeiro está em seu bucket,
na pasta um, subpasta um arquivo com barra.
Nesse caso, o prefixo será qualquer coisa
entre o bucket e o arquivo.
Portanto, nesse caso, é a pasta com barra um, barra sub um.
Portanto, isso significa que, para esse arquivo
nesse prefixo, você pode obter 3.500 Puts e 5.500 Gets por segundo.
Agora, se tivermos outra pasta um e depois sub dois, o prefixo
é qualquer coisa entre buckets e file, então barra
pasta um barra sub dois, e assim teremos
também 3.500 Puts e 5.500 Gets para esse prefixo, e assim
por diante.
Portanto, se eu tiver um e dois, teremos prefixos diferentes,
e assim fica fácil entender o que é um prefixo,
e assim fica fácil entender a regra de 3.500 Puts e 5.500
Gets por segundo por prefixo em um bucket.
Isso significa que, se você distribuir
as leituras pelos quatro prefixos acima de maneira uniforme,
poderá obter 22.000 solicitações por segundo para
Head and Gets.
Agora, vamos falar sobre o desempenho
do S3, como podemos otimizá-lo?
O primeiro é o upload de várias partes.
Portanto, é recomendável usar o upload de
várias partes para arquivos com mais de 100 megabytes,
e ele deve ser usado para arquivos com mais de cinco gigabytes.
E o que o upload de várias partes
faz é paralelizar os uploads, o que nos ajudará a acelerar
as transferências para maximizar a largura de banda.
Portanto, como um diagrama, ele sempre faz mais sentido.
Portanto, temos um arquivo de bytes
e queremos fazer upload desse arquivo no Amazon S3.
Vamos dividi-lo em partes, portanto, pedaços menores desses arquivos
e cada um desses arquivos será carregado
em paralelo no Amazon S3.
No Amazon S3, uma vez que todas as partes tenham sido carregadas,
ele é inteligente o suficiente para juntá-las novamente
em um arquivo grande.
Ok, muito importante.
Agora, temos a aceleração de transferência
do S3, que é para upload e download e serve
para aumentar a velocidade de transferência
ao transferir um arquivo para um local de borda do AWS, que encaminhará
os dados para o bucket do S3 na região
de destino.
Portanto, há mais locais de borda do que regiões.
Atualmente, há mais de 200 locais de borda, e isso está crescendo,
e deixe-me mostrar no gráfico
o que isso significa...
E essa aceleração de transferência S3 é
compatível com o upload de várias partes.
Então, vamos dar uma olhada.
Temos um arquivo nos Estados Unidos da América
e queremos carregá-lo em um bucket S3 na Austrália.
Portanto, o que isso fará é carregar esse arquivo por meio de um local
de borda nos Estados Unidos, o que será muito,
muito rápido, e então usaremos
a Internet pública.
E, em seguida, desse local de borda
para o bucket do Amazon S3 na Austrália,
o local de borda o transferirá
pela rede rápida e privada do AWS.
Portanto, isso se chama aceleração
de transferência, porque minimizamos a quantidade de Internet
pública pela qual passamos e maximizamos a quantidade
de rede AWS privada pela qual passamos.
Portanto, a aceleração de transferência
é uma ótima maneira de acelerar as transferências.
Agora, que tal obter os arquivos?
Que tal ler o arquivo da maneira mais eficiente possível?
Temos algo chamado S3 Byte Range Fetches, que serve para paralisar
os Gets, obtendo intervalos de
bytes específicos para seus arquivos.
Portanto, se você não conseguir obter um intervalo
de bytes específico, poderá tentar
novamente um intervalo de bytes menor e
terá maior resiliência em caso de falhas.
Portanto, ele pode ser usado para acelerar os downloads desta vez.
Então, vamos tentar um arquivo no S3, ele é muito,
muito grande e este é o arquivo.
Talvez você queira solicitar a primeira
parte, que são os primeiros bytes do arquivo,
depois a segunda parte e, em seguida, as partes finais.
Portanto, solicitamos todas essas partes como
buscas específicas de intervalo de bytes, por isso é chamado
de intervalo de bytes, porque solicitamos apenas um intervalo
específico do arquivo.
E todas essas solicitações podem ser feitas em paralelo.
Portanto, a ideia é que possamos paralelizar os
Gets e acelerar os downloads.
O segundo caso de uso é recuperar apenas
uma parte do arquivo.
Por exemplo, se você sabe que os primeiros 50 bytes do arquivo
no S3 são um cabeçalho e fornecem algumas informações
sobre o arquivo, basta emitir uma solicitação
de cabeçalho para uma solicitação de intervalo
de bytes para os cabeçalhos usando os primeiros
50 bytes e você obterá essas informações
muito rapidamente.
Muito bem, então é isso para o desempenho do S3.
Já vimos como acelerar os uploads e downloads.
Vimos o desempenho da linha de
base e vimos os limites do KMS.
Portanto, certifique-se de que você saiba isso ao
fazer o exame e nos veremos na próxima aula.
