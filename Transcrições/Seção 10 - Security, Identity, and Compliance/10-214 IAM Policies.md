Então, vamos imaginar que temos um grupo
de desenvolvedores, Alice, Bob
e Charles, e anexamos uma política no nível do grupo.
Nesse caso, a política será
aplicada a todos os membros
do grupo, de modo que Alice, Bob e Charles
terão acesso e herdarão essa política.
Agora, se você tiver um segundo grupo com operações
com uma política diferente, David
e Edward terão uma política diferente da do
grupo de desenvolvedores.
Se Fred for um usuário, ele tem a possibilidade
de não pertencer a um grupo.
E temos a possibilidade de criar o que
chamamos de política em linha, que tem uma
política que é anexada apenas a um usuário.
Para que esse usuário possa ou não pertencer
a um grupo, você pode ter políticas em linha para qualquer usuário que desejar.
E, finalmente, se Charles e David pertencerem à equipe
de auditoria e você anexar uma política à equipe de auditoria,
Charles e David também herdarão essa política da equipe
de auditoria.
Portanto, nesse caso, Charles tem uma política dos desenvolvedores
e uma política da equipe de auditoria.
E David tem uma política da equipe de
auditoria e uma política da equipe de operações.
Isso deve fazer muito
sentido quando entrarmos na prática.
Agora, em termos de estrutura de política,
você só precisa saber em alto nível como ela
funciona e como é nomeada.
Isso é algo que você verá bastante na AWS, portanto, familiarize-se
com essa estrutura, que são os documentos
adjacentes.
Portanto, uma estrutura de política
de IAM consiste em um número de versão, geralmente 2012-10-17,
que é a versão do idioma da política.
E o ID, que é como identificar essa política, é
opcional.
E depois mais declarações, e as declarações
podem ser uma ou várias, e uma declaração tem algumas partes
muito importantes.
Assim, o Sid é um ID de declaração, que é um identificador para a declaração,
que também é opcional, portanto,
no lado direito está o número um.
O efeito da política em si, ou seja, se a declaração permite ou nega o acesso
a determinada API, portanto, no lado direito, está escrito
allow (permitir), mas você também pode
ver deny (negar).
O princípio consiste em quais contas, usuários ou funções,
aos quais essa política será aplicada.
Portanto, neste exemplo, ele é aplicado às
contas raiz de suas contas do AWS.
Action é a lista de chamadas de API que serão
negadas ou permitidas com base no efeito.
E o recurso é uma lista de recursos aos quais
as ações serão aplicadas.
Portanto, neste exemplo, é um balde, mas poderia
ser muitas coisas diferentes.
E, finalmente, não está representado
aqui, mas há uma condição para a qual essa
declaração deve ser aplicada ou não, e isso não é representativo
aqui porque é opcional.
Portanto, ao fazer o exame, você precisa
ter certeza de que realmente entende o efeito, o princípio,
a ação e o recurso, mas não se preocupe, pois
você verá esses elementos ao longo do curso e, portanto,
deverá estar confiante com eles ao final do
curso.
É isso para esta palestra, espero que você tenha gostado.
E eu o verei na próxima palestra.
