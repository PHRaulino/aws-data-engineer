muitos nós de computação e em muitas fatias dentro desses nós.
Agora, há várias maneiras diferentes de fazer essa distribuição que você precisa entender.
Portanto, quando os dados forem carregados em uma tabela, o redshift distribuirá as linhas da tabela para os nós de
computação e fatias de acordo com o estilo de distribuição que você escolheu quando criou a tabela.
Os dois principais objetivos da distribuição de dados são distribuir a carga de trabalho uniformemente
entre os nós do cluster e minimizar a movimentação de dados durante a execução da consulta.
Há quatro estilos diferentes de distribuição, que são os seguintes.
Distribuição automática.
Se você não especificar um estilo de distribuição, o Amazon Redshift usará a distribuição automática
e, com base no tamanho dos dados da tabela, o Redshift atribuirá um estilo de distribuição ideal para você,
que pode ser a chave par ou todas.
Portanto, vamos nos aprofundar em cada um deles de forma independente.
Primeiro, vamos falar sobre distribuição uniforme.
Para que haja uma distribuição uniforme, independentemente dos valores em qualquer coluna específica, o nó
líder distribui as linhas entre as fatias de forma circular.
Portanto, ele percorrerá cada fatia individual e continuará atribuindo novos dados a cada fatia
de forma circular.
Isso é apropriado quando uma tabela não participa de uniões ou quando não há uma escolha clara entre
a distribuição de chaves ou toda a distribuição.
Portanto, até mesmo a distribuição tenta distribuir as coisas da forma mais uniforme possível, sem pensar
em tentar agrupar os dados que podem ser acessados ao mesmo tempo.
Distribuição de chaves.
Aqui, as linhas são distribuídas de acordo com os valores em uma coluna, de modo que o nó líder colocará os valores
correspondentes no mesmo nó.
Os valores de fatia e correspondência das colunas comuns são armazenados fisicamente juntos, portanto, isso pode
ser útil se você costuma fazer consultas com base em uma coluna específica dos seus dados.
Ao usar a distribuição de chaves, você pode ter certeza de que todos os dados associados a um valor de chave específico
estarão fisicamente localizados na mesma fatia, o que pode acelerar suas consultas.
Portanto, o diagrama aqui mostra que, à medida que novas linhas forem chegando dos dados recebidos, essas chaves serão transformadas em hash
e definidas para uma fatia específica com base em como essa chave é transformada em hash.
Então, temos toda a distribuição e, com toda a distribuição, uma cópia da tabela inteira é distribuída
para cada nó.
Isso garante que cada linha seja co-localizada.
Para cada junção da qual a tabela participa, a distribuição all multiplica o armazenamento necessário pelo
número de nós no cluster, portanto, leva muito mais tempo para carregar, atualizar ou inserir dados em várias
tabelas.
Toda a distribuição é realmente apropriada apenas para tabelas de movimento relativamente lento, ou seja, tabelas que não
são atualizadas com frequência ou extensivamente.
Como o custo da redistribuição é baixo, as tabelas de dimensões pequenas não se beneficiam significativamente de toda
a distribuição.
Agora, se você precisar visualizar o estilo de distribuição de uma tabela, poderá consultar a visualização de informações da classe
PG ou a visualização de informações da tabela SV.
A coluna Reflective Style nas informações da classe PG indicará o estilo de distribuição atual para essa tabela.
