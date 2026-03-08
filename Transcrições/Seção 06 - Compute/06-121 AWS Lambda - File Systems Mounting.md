Portanto, suas funções Lambda podem acessar o sistema de arquivos EFS
se estiverem sendo executadas em uma VPC.
Para isso, basta configurar o Lambda
para montar o sistema de arquivos EFS em um diretório local
durante a inicialização do ano.
Para que isso funcione,
você deve aproveitar o recurso de pontos de acesso EFS do EFS.
Então, digamos que você tenha um sistema de
arquivos EFS e crie um ponto de acesso EFS.
Então, se as funções do Lambda
forem implantadas em uma sub-rede privada
que tenha conectividade privada com a sua VPC, você
estará pronto para começar.
A limitação disso é que, para cada instância
do Lambda que surgir, você terá mais uma conexão com o
sistema de arquivos EFS, portanto,
é preciso garantir que não
atinja os limites de conexão
do EFS.
Além disso, se você tiver muitas funções Lambda diferentes
que surgem de uma só vez, como uma explosão,
também poderá atingir os limites de explosão de conexão.
Portanto, quero dedicar algum tempo para
comparar as opções de armazenamento para
o Lambda, para que você possa entender qual
delas é a melhor com base na situação.
Portanto, o armazenamento efêmero de /tmp tem
um tamanho máximo de 10 gigabytes, o que é muito.
A persistência é efêmera, o que
significa que, assim que a instância da função Lambda for
destruída, você perderá o armazenamento.
É por isso que ele é chamado de /tmp, para temporário.
O conteúdo é dinâmico, você pode modificá-lo como quiser.
É um sistema de arquivos
e suporta qualquer operação do sistema de arquivos.
Ele está incluído para sua função Lambda até 512 megabytes
e você paga pelo adicional
se tiver mais de 512 megabytes.
E somente a sua função tem acesso a ele, porque
ele diz que o armazenamento é baseado na sua função Lambda.
Esse é o nível mais rápido de recuperação de dados e não é compartilhado
em todas as suas invocações
de funções Lambda.
Portanto, isso deve fazer sentido.
Agora, suas camadas Lambda.
O tamanho máximo é de cinco camadas
por função, com um total de até 250
megabytes para não exceder o tamanho máximo do pacote Lambda.
E a persistência é durável porque é imutável, você não
pode alterar o que entra em uma Lambda Layer.
Portanto, ele é do tipo archive, é estático
e está incluído no preço da função Lambda.
E, para obter acesso a uma camada, você precisa
ter certeza de que possui as permissões de IAM adequadas.
Também é a velocidade mais rápida para acessar os
dados na camada, porque ela é anexada
como armazenamento à sua função Lambda e é compartilhada em todas as
suas invocações do Lambda, portanto, todas elas são compartilhadas,
lembre-se.
Você não pode modificar dados na camada Lambda.
Se você estiver usando o Amazon
S3, poderá ter o tamanho que quiser, pois o
tamanho é durável e dinâmico.
O tipo de armazenamento é Objeto, portanto, você precisa usar
a API do S3 para acessar os objetos do Amazon S3.
Além disso, há as operações atômicas, para que você possa
obter, colocar, publicar e assim por diante, com controle de versão.
Pelo preço que você paga, é claro, pelo preço do Amazon S3, portanto,
armazenamento mais solicitações, mais transferência de dados.
E para obter acesso ao Amazon S3, você precisa
ter certeza de que possui as permissões IAM adequadas.
Esse é um armazenamento baseado em rede.
Portanto, temos um acesso rápido
porque temos largura de banda dedicada
da AWS, mas não é o mais rápido.
E, é claro, o Amazon
S3 é compartilhado em todas as suas invocações Lambda
porque, bem, ele é um armazenamento externo de dados.
Por fim, para o Amazon EFS, temos o Elastic.
É durável, é dinâmico.
O tipo de armazenamento é o sistema de arquivos,
portanto, nós o acessamos usando qualquer tipo de operação do sistema de arquivos.
Vamos pagar pelo armazenamento, pela
transferência de dados e pela taxa de transferência.
E como ele é montado como um sistema
de arquivos de rede em sua função
Lambda, você terá acesso muito rápido aos seus dados.
Por fim, como se trata de um sistema de arquivos
de rede, ele será compartilhado
em todas as suas Lambda Invocations.
Esperamos que isso faça sentido
para as diferentes opções de armazenamento do Lambda.
Espero que tenham gostado e nos veremos na próxima palestra.
