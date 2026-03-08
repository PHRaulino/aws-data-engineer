Agora vamos dar uma olhada no
DynamoDB, que é um banco de dados NoSQL sem servidor.
Portanto, se considerarmos a arquitetura
tradicional que vimos neste curso,
temos clientes e eles se conectam a uma camada de aplicativos que pode ser
composta por um balanceador de carga elástico e instâncias
EC2 agrupadas e dimensionadas com um grupo de dimensionamento
automático.
E, em seguida, os dados precisam ser
obtidos em algum lugar, portanto,
temos uma camada de banco de dados, que pode usar
o Amazon RDS, que é apoiado pelo MySQL, ou PostgreSQL,
ou esse tipo de tecnologia.
Esses aplicativos tradicionais
aproveitam os bancos de dados RDBMS, e fazemos isso
porque temos a linguagem de consulta SQL.
É muito bom.
E, então, podemos definir requisitos rigorosos sobre
como os dados devem ser modelados,
pois temos tabelas, esquemas e assim por diante.
Podemos fazer junções, agregações, cálculos complexos, e tudo
isso é muito bom e está funcionando.
No entanto, o que obtemos com isso,
no caso de escalonamento, é principalmente o escalonamento vertical.
Portanto, caso você queira um banco de dados melhor, e estou
falando apenas de uma camada de banco de dados neste momento.
Se quiser dimensioná-lo verticalmente,
você precisará substituir o banco
de dados e obter uma CPU mais potente, mais memória RAM
ou um disco melhor com IO.
E você pode fazer algum tipo de escalonamento horizontal,
mas isso é feito apenas aumentando a capacidade de leitura.
Portanto, adicionando instâncias do EC2 na camada
do aplicativo ou adicionando réplicas
de leitura do RDS nas camadas do banco de dados.
Mas se você adicionar réplicas de leitura,
ficará limitado pelo
número de réplicas que pode ter e, portanto,
no dimensionamento horizontal à direita,
pois isso não existe no RDS.
Portanto, apresento a vocês os bancos de dados NoSQL,
que significam não apenas bancos de dados SQL ou não SQL,
dependendo da definição.
Portanto, a ideia é que existam bancos de dados não relacionais
e que eles sejam distribuídos,
o que nos dá alguma escalabilidade horizontal.
E algumas tecnologias muito
famosas que têm bancos de dados NoSQL são o MongoDB
e, é claro, o DynamoDB.
Atualmente, esses bancos de dados não oferecem suporte a articulações de consulta
ou têm suporte muito limitado.
Portanto, para simplificar,
suponhamos que eles não tenham uniões de consultas.
Agora, todos os dados necessários
devem estar presentes em uma linha no seu banco de dados.
E, novamente, para simplificar as coisas, sei que elas estão evoluindo,
mas vamos supor que os bancos de dados
NoSQL também não realizam cálculos de agregação,
como SUM, AVG e assim por diante.
Mas o bom disso é que, graças ao design, os bancos de dados
NoSQL serão dimensionados horizontalmente.
Isso significa que, se você precisar de mais capacidade
de leitura ou de direito, poderá, nos bastidores, ter mais instâncias
e isso será muito bem dimensionado.
Portanto, não há certo ou errado para NoSQL vs. SQL,
depende apenas de como você pensa sobre
a modelagem de dados, sobre o aplicativo, sobre as consultas
dos usuários e sobre as necessidades de dimensionamento.
Então, vamos falar sobre o DynamoDB agora.
Portanto, o DynamoDB é um banco de dados NoSQL totalmente gerenciado,
altamente disponível
e com replicações em várias AZs prontas para uso.
Portanto, é um banco de dados NoSQL.
Não é um banco de dados relacional.
Portanto, é diferente do RDS.
Ele é dimensionado para cargas de trabalho enormes e é totalmente distribuído.
Isso significa que você
pode escalonar para milhões de solicitações
por segundo, trilhões de linhas e centenas de terabytes de armazenamento,
independentemente da sua carga de trabalho.
Desempenho muito rápido e consistente.
Isso significa que você obtém uma latência muito baixa na recuperação.
E é um serviço, portanto,
será totalmente integrado ao IAM para segurança,
autorização e administração.
Você pode ativar a programação orientada
a eventos com o DynamoDB Streams, como veremos nesta seção.
É de baixo custo e tem capacidade de dimensionamento automático.
E você tem a classe de tabela
IA padrão e de acesso infrequente para diferentes
níveis de armazenamento.
Então, vamos dar uma olhada nos conceitos básicos do DynamoDB.
Portanto, o DynamoDB é feito de tabelas e cada
tabela terá uma chave primária.
E veremos o que pode ser a chave primária
nos próximos slides.
Você deve decidir qual é a chave
primária antes de criar a tabela.
Agora, cada tabela pode ter um número infinito de linhas, também
chamadas de itens.
Portanto, neste curso, usarei os termos linhas e itens
de forma intercambiável,
e cada item terá atributos.
Esses atributos podem ser semelhantes
às colunas de sua tabela, certo?
Mas esses atributos também podem ser aninhados.
Portanto, é um pouco mais poderoso do que as colunas,
e elas podem ser adicionadas ao
longo do tempo, você não precisa
defini-las todas no momento da criação da tabela,
e algumas delas podem ser nulas.
portanto, não há problema algum em
um atributo estar ausente em alguns dados.
Agora, cada item ou cada
linha terá até 400 kilobytes de dados, portanto,
é uma limitação.
E os tipos de dados suportados serão tipos escalares,
ou string, número, binário, booleano e nulo.
Haverá tipos de documentos, como listas e mapas,
o que lhe dá algum tipo de capacidade de aninhamento.
E tipos de conjuntos, como conjuntos de strings,
conjuntos de números e conjuntos binários.
Agora, um ponto muito importante a ser entendido
é como escolher uma chave primária para o DynamoDB.
E o exame certamente testará
seu conhecimento sobre isso.
Portanto, você tem duas opções para chaves primárias.
E a primeira é chamada de chave de partição, que
também é chamada de estratégia de hash.
Portanto, a chave de partição, nesse caso, deve ser exclusiva
para cada item, o que é muito semelhante a um banco de dados normal.
Portanto, a partição
deve ser diversificada o suficiente
para que seus dados sejam distribuídos.
Por exemplo, se considerarmos
user_ID para a tabela de usuários, poderemos ter a chave
de partição como sendo User_ID.
O atributo está sendo First-Name, Last_Name e age.
E então você tem seu primeiro ID de usuário com
alguns atributos sendo preenchidos.
Seu segundo User_ID, como você pode
ver, não tem um sobrenome,
mas isso não tem problema no DynamoDB.
E a terceira chave de partição,
mais uma vez, tem três atributos associados a ela.
Portanto, esta é a aparência do DynamoDB.
Por enquanto, parece ser um banco de dados.
É muito fácil.
Mas você poderia ter uma segunda opção de
chave de partição e chave de classificação, também
chamada de hash mais intervalo.
E agora a combinação desses dois itens deve ser exclusiva
para cada item.
Portanto, os dados serão agrupados por chave de partição.
Por isso, é muito importante
escolher uma boa chave de partição.
Portanto, se você considerar uma tabela users-game, então User_ID
para a chave de partição e Game_ID para a chave
de classificação.
Vamos ver o que isso significa.
Isso significa que os usuários podem assistir a vários jogos.
Portanto, temos esses atributos de quatro colunas, mas a primeira
será nossa chave de partição.
Queremos que os dados sejam agrupados
por User_ID, e o segundo será uma chave de classificação.
Isso nos dará a exclusividade da
combinação da chave de partição e da chave de classificação.
Portanto, ambos farão a chave primária
e os demais serão atributos.
Portanto, se considerarmos um User_ID, ele
tem uma chave de classificação que estava no Game_ID e,
em seguida, atribuímos a pontuação 92, o resultado vitória.
Novamente, outro User_ID diferente e outro Game_ID
diferente, portanto, isso também
funciona.
Você tem um jogo perdido com uma pontuação de 14.
E o mais interessante é que, nessa terceira linha,
temos a mesma chave de partição.
Portanto, as linhas dois e três têm a mesma chave de partição, mas uma chave
de classificação diferente.
É claro que não há problema em um usuário assistir a vários jogos.
Portanto, você deseja
que a combinação de User_ID
e Game_ID seja exclusiva, obviamente, mas também
não há problema em ter a mesma chave de partição em uma chave
de classificação diferente.
E é por isso que é muito importante
escolher uma chave de partição realmente boa,
para que os dados sejam distribuídos o suficiente.
Portanto, aqui está um exercício,
e é sobre isso que o exame também poderá testá-lo.
Portanto, você está criando um banco de dados
de filmes e deseja escolher a melhor chave de partição
para maximizar a distribuição de dados.
É o movie_id?
É o nome do produtor?
É o nome do ator líder ou o idioma do filme?
Bem, pense nisso por um segundo: e se você escolher
a primeira, escolher
a segunda e assim por diante?
Agora, a resposta é escolher movie_id,
porque movie_id será exclusivo para cada linha.
Portanto, é um ótimo candidato
para particionar sua tabela.
Se você tiver um idioma de filme como, desculpe, uma chave de partição, não
terá tantos valores quanto deseja, e talvez a maioria
dos seus filmes seja
em inglês.
Portanto, não será uma ótima
escolha porque não há diversidade
suficiente e há uma inclinação dos dados para um valor específico.
Assim, o exame pedirá que você escolha a melhor
chave de partição para algumas tabelas com base no
que ela significa.
Portanto, sempre escolha o que tiver a maior cardinalidade
e o que puder assumir a maior quantidade de valores.
Então é isso para uma breve visão geral do DynamoDB.
Temos uma longa seção sobre isso,
mas vamos ver a parte prática para praticar
um pouco o uso do DynamoDB.
