Então, vamos falar rapidamente sobre o PartiQL for DynamoDB, que
permite que você use uma sintaxe semelhante à do SQL
para manipular as tabelas do DynamoDB.
Portanto, é assim que as declarações se pareceriam.
E, a partir disso, você pode inserir, por exemplo,
Portanto, é para permitir que as pessoas mais
confiantes no uso do SQL ainda possam interagir com o DynamoDB.
E ele também suporta operações em lote, se necessário.
Então, deixe-me mostrar como o PartiQL funciona no console.
Então, estou em minhas tabelas,
e o lado esquerdo é o editor PartiQL.
Então, vamos abrir algumas
dessas tabelas, por exemplo, vamos abrir a tabela do usuário
e eu a esvaziei, mas posso, por exemplo, adicionar
um item rapidamente, para que eu possa ter um user_id 123, bem como um novo
atributo, nome, Stephan, e isso é bom.
E para a minha outra tabela, a postagem do usuário,
posso novamente adicionar alguns
itens, então user_id 123 post_id 456 e criar o
item, assim como para os índices de demonstração,
posso criar um item user_id
123 game times stamp 2022, mesmo que não seja muito bom.
E depois game_id 456.
Está bem. Então, criei alguns itens em todas
as minhas tabelas e, agora, se você for ao editor PartiQL, poderemos
ver, por exemplo, a tabela do usuário e eu poderei excluí-la.
Clico em usuários, faço uma varredura na
tabela e ela tem um select start
from users, que é uma instrução SQL.
E se eu o executar,
ele diz que a declaração não foi bem formada.
Portanto, agora ele está concluído e você
pode ver que o resultado dos itens está definido e o user_id 123, que também pode
ser obtido na exibição adjascent, se você quiser,
porque é isso que seria
usado em seu código para lidar com ele.
E podemos fazer o download dos resultados em um arquivo CSV.
Em seguida, para coisas mais complicadas,
você pode examinar a tabela de índices de demonstração,
e podemos fazer a varredura dessa tabela
novamente, para que possamos ver todos os itens.
Mas você pode fazer coisas
mais interessantes, por exemplo, pode consultar
a tabela e, quando você consulta a tabela, ela gera uma declaração
e diz: início sólido de índices de demonstração, em que user_id é igual
a, por exemplo, 1,2,3, e você também
pode ter um carimbo de data/hora de fim de jogo igual ao valor da
chave Sort, mas isso é opcional.
E se você executar isso, obviamente,
obteremos os itens corretos.
Assim, podemos começar
a criar algumas consultas bem complicadas, mas, como temos um índice aqui, podemos
usar esse índice e fazer a varredura.
Portanto, podemos selecionar start from demo indexes e, em seguida,
o nome do índice.
E ele retornará o item com base no meu índice.
E você pode fazer muitas coisas,
pode executar instruções de inserção, embora
não seja fácil executá-las diretamente na
interface do usuário porque elas não são geradas automaticamente.
Também é possível definir um item, de modo que você possa atualizar um item específico
e definir o valor do atributo, o valor da chave de partição e o valor da
chave de classificação e assim por diante.
Ou você pode, por exemplo,
eliminar um item específico e ter um comando delete from.
Portanto, este editor é apenas para pessoas que desejam
usar o SQL no DinamoDB.
Gostaria apenas de acionar o recurso muito rapidamente.
Está bem. É isso aí.
Espero que tenham gostado
e nos veremos na próxima palestra.
