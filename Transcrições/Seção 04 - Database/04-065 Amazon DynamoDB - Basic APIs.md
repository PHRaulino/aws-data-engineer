No exame, você verá as chamadas
de IPI do DynamoDB mencionadas pelo nome.
Portanto, é bom para nós vê-los uma vez.
Portanto, se quiser gravar dados, você tem algumas opções.
Você tem o PutItem e, quando faz um PutItem,
ele cria ou substitui totalmente um novo item que tem a
mesma chave primária.
Portanto, a ideia é que você queira fazer uma substituição
completa ou escrever um novo item.
O segundo é o UpdateItem, que
é um pouco diferente do PutItem.
Essa opção editará os itens e atributos existentes ou adicionará
um novo item, caso ele não exista.
Mas a ideia é que, com o UpdateItem, editamos
apenas alguns atributos, não todos os outros atributos.
Portanto, essa é a diferença entre PutItem e UpdateItem.
E também podemos usá-lo com os Atomic Counters
que veremos nesta seção.
E há também as gravações condicionais,
que aceitam uma gravação/atualização/exclusão
somente se uma condição for atendida.
E isso está ajudando no acesso simultâneo aos itens.
E veremos isso também nesta seção.
Para ler dados, temos um GetItem.
E o GetItem é muito simples e fácil de entender.
Você lê com base na chave primária e a chave primária, mais uma vez,
pode ser um HASH ou um HASH+Range, portanto,
você tem duas opções.
E você tem dois modos de leitura.
Portanto, você tem o Eventually Consistent Read Mode (modo de leitura eventualmente consistente)
ou o Strongly Consistent Read Modes (modos de leitura fortemente consistentes), mas
precisa especificá-lo.
Isso exigirá mais RCU e, talvez,
um pouco mais de latência.
Você também pode especificar uma Expressão projetada em sua API.
E essa expressão de projeção
o ajudará a receber apenas alguns atributos
do DynamoDB.
Em seguida, temos a consulta.
E a consulta deve retornar itens com
base em uma expressão de condição de chave, que é uma chave
de partição, portanto, deve ser o operador igual.
Então você está dizendo: "Ei, quero consultar João 123"
e, opcionalmente, uma chave de classificação e, como
você pode classificar, pode ter igual, menor que, maior que,
começa, entre e assim por diante.
Em seguida, você pode especificar uma FilterExpression.
E isso serve para adicionar filtragem adicional
após a operação de consulta ter sido feita, mas antes
de os dados serem retornados a você.
E isso é para ser usado com atributos não-chave.
Portanto, você não pode usar uma FilterExpression
com atributos HASH ou RANGE.
E o que a consulta retorna
será uma lista de itens, obviamente.
E você tem um limite de quantos itens recupera
com base no parâmetro de consulta limit.
E você atingirá esse
limite de nunca itens
ou chegará a um Megabyte de dados.
Mas se você quiser obter, obviamente, mais dados do seu tempo,
poderá fazer a paginação dos resultados
e solicitar mais e mais e mais.
Agora você pode consultar uma
tabela, um índice secundário local ou um índice secundário
global, e veremos isso também nas próximas aulas.
E, por fim, você tem uma varredura, de modo que GetItem era para um item e, em seguida,
a consulta era para uma chave de partição específica e uma chave
de classificação.
E o Scan items é para ler uma tabela inteira.
E, se você quisesse, poderia filtrar os dados, mas
isso só é feito no lado do cliente,
o que é muito ineficiente.
Portanto, o Scan é realmente exportar a tabela inteira.
E cada varredura retornará até um megabyte de dados e,
se você quiser continuar lendo, precisará
usar técnicas de paginação.
Isso significa página um, página dois, página três e assim por diante.
Isso consumirá muita RCU
porque você está lendo toda a sua tabela.
Portanto, se você
não quiser afetar suas operações normais, precisará
afetar a varredura usando uma instrução de limite ou para reduzir o tamanho do
resultado e, em seguida, fazer
uma pequena pausa.
E se, em vez disso, você quisesse consumir
muitas RCUs e fazer uma varredura o mais rápido possível, então, para obter um desempenho
mais rápido, você usaria uma varredura paralela.
Nesse caso, vários workers que você definir farão
a varredura de vários segmentos de dados ao mesmo tempo, o que
aumentará a taxa de transferência e a RCU consumida.
E, se você ainda quisesse ter uma varredura paralela
e limitar seu impacto, poderia
usar consultas limitadas, condições limitadas e assim por diante.
E as varreduras podem ser usadas com ProjectionExpression
e FilterExpression.
Portanto, ProjectionExpression para recuperar apenas determinados
atributos e FilterExpression para alterar as coisas no lado do servidor.
Agora, se você precisar excluir dados do DynamoDB, você
tem o DeleteItem, que
é usado para excluir um item individual.
E, em seguida, você também pode fazer uma exclusão
condicional, ou seja, excluir esse item somente se o dinheiro for igual a zero.
E se você precisar excluir tudo da tabela,
você tem o DeleteTable.
Portanto, isso é para excluir uma tabela inteira e seu item.
E isso é muito mais rápido do que fazer uma
varredura e depois excluir cada item da tabela.
Certo, DeleteTable, que simplesmente eliminará tudo.
E isso é algo que pode surgir no exame.
Se você quiser apenas excluir tudo, não
faça uma varredura, apenas use a API DeleteTable.
Agora, para fins de eficiência, você
pode realmente realizar operações em lote no DynamoDB.
Assim, você economiza em latência e obtém eficiência
ao reduzir o número de chamadas de API que faz para o banco de dados.
E todas as operações, como parte de um
lote, serão aplicadas em paralelo pelo DynamoDB para
maior eficiência.
Portanto, como você tem um lote de operações,
parte do lote pode falhar.
Nesse caso, você receberá os itens com falha de volta e
poderá tentar novamente apenas esses itens com falha.
Portanto, no mecanismo correto, você tem
o BatchWriteItem, que permite executar até 25 PutItem
e/ou DeleteItem em uma única chamada.
Você tem até 16 megabytes de dados gravados
e ainda tem o mesmo limite de 400 kilobytes de
dados por item.
E você não pode atualizar
o item, só pode fazer PutItem ou DeleteItem.
Agora, se você tiver itens que não puderam ser gravados por qualquer
motivo, geralmente
por falta de capacidade de gravação, você receberá de
volta algo chamado UnprocessedItems,
e poderá tentar novamente os
itens dentro dos UnprocessedItems.
Portanto, há duas opções para processá-los corretamente.
Ou você usa uma estratégia de backup exponencial
para continuar tentando com um tempo cada vez maior
até obter sucesso, ou se você
recebe constantemente esses UnprocessedItems e problemas de dimensionamento,
então, é claro, você precisa adicionar unidades
de capacidade de gravação para permitir que
suas operações em lote sejam concluídas com eficiência.
Para GetItem em lote, você
retornará itens de uma ou mais tabelas e poderá
receber até 100 itens e até 16
megabytes de dados.
E todos esses itens serão recuperados em paralelo
para minimizar a latência.
Novamente, se estiverem faltando alguns itens,
é porque você pode ter algumas UnprocessedKeys porque
houve falha nas operações de leitura por
não ter capacidade suficiente.
Nesse caso, a ideia é a mesma: você usa o backup
exponencial para tentar novamente ou adiciona unidades
de capacidade de leitura para aumentar
sua capacidade de leitura.
Além disso, temos o PartiQL.
Portanto, vimos que no DynamoDB
temos chamadas de API específicas para fazer coisas específicas,
mas, às vezes, tudo o que você sabe, como
engenheiro de dados ou qualquer outra coisa, como desenvolvedor, pode ser SQL.
Assim, você pode usar o SQL no DynamoDB usando o PartiQL.
Portanto, aqui você tem uma consulta SQL padrão
em que encontra o OrderID e o Total
da tabela Orders, e tem uma condição
de filtragem e uma condição
de ordenação.
Assim, usando o PartiQL, você pode
fazer exatamente as mesmas operações que vimos antes,
ou seja, selecionar, inserir, atualizar e excluir
dados no DynamoDB.
Mas, desta vez, em vez de usar as APIs específicas do DynamoDB, você
pode usar apenas o SQL.
E você pode executar suas consultas
em várias tabelas do DynamoDB, mas não pode fazer
junções, certo?
Você pode simplesmente selecionar, inserir, atualizar e excluir.
Tudo o que você pode fazer com
uma API, mas você usa SQL para escrever essas chamadas.
Portanto, você executa consultas PartiQL
no Management Console ou no NoSQL Workbench
for DynamoDB, nas APIs do DynamoDB, na CLI ou no SDK.
E o objetivo disso
não é realmente adicionar novos recursos ao DynamoDB,
porque você tem os mesmos recursos,
mas é apenas usar o SQL para
escrever essas chamadas de API no DynamoDB.
Espero que isso faça sentido.
Espero que tenham gostado e nos veremos na próxima palestra.
