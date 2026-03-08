Certo, agora vamos falar sobre índices para o DynamoDB,
e você tem dois tipos de índices que precisa conhecer.
O primeiro é um índice secundário local.
Portanto, o LSI lhe dará uma chave de classificação alternativa para
sua tabela.
Portanto, você tem a mesma chave de partição da tabela base,
E essa chave de classificação consiste em um atributo escalar.
Pode ser uma cadeia de caracteres, um número
ou um binário, e você pode obter até cinco LSIs por tabela.
Agora, os LSIs devem ser definidos no momento da criação da tabela.
Portanto, você não pode criá-las depois que as tabelas forem criadas.
Portanto, você precisa pensar cuidadosamente
em como deseja que sua mesa seja projetada.
Em seguida, no seu LSI, você pode ter alguns ou todos os atributos
da sua tabela principal.
Portanto, cabe a você escolher em seu LSI.
Se você quiser ter apenas um atributo específico, porque
é isso que você está tentando consultar.
Então, se pegarmos um exemplo aqui, esta é a nossa tabela,
que tem o ID do usuário, o ID do jogo, o registro de data e hora do jogo,
a pontuação e os resultados.
No momento, podemos fazer consultas sobre o ID do usuário e o ID do jogo, o que
é muito simples, mas não podemos
fazer uma consulta sobre o ID do usuário e o carimbo de data/hora do jogo.
Para isso, precisamos fazer uma
varredura e, em seguida, uma filtragem
do lado do serviço e do site do cliente.
Então, para fazer isso, se você quiser fazer uma consulta com base no ID do usuário e no carimbo
de data/hora do jogo.
Precisaríamos criar um LSI e definir o LSI nos atributos
de registro de data e hora do jogo.
E, se fizermos isso, poderemos fazer uma
consulta sobre, ei, me dê todos os jogos que foram feitos
por esse usuário entre 2021 e 2020 e assim por diante, ok.
Portanto, é muito importante que você
entenda que essa é a mesma chave de partição
de antes, mas temos um tipo diferente de chave para um LSI.
Em seguida, temos o GSI ou índices secundários globais.
Isso lhe dará uma chave primária diferente,
ou seja, alternativa.
Portanto, você pode ter uma chave de hash diferente,
uma chave de partição diferente
ou pode ter uma chave de hash diferente e uma chave de classificação também diferente.
Na tabela de base.
Portanto, isso é útil se você quiser acelerar as consultas
sobre itens que não são atributos-chave em sua tabela.
Portanto, o índice pode causar esse aumento nos atributos
do número de tensão em binário.
E, novamente, você pode especificar quais
atributos deseja projetar nesse índice.
No entanto, para esse índice, ele é muito
especial porque é como se fosse uma nova tabela diferente.
Portanto, para esse índice,
você deve provisionar as RCUs e WCUs.
Agora, os GSI são poderosos porque podem
ser adicionados ou modificados após a criação da tabela.
Então, vamos usar uma tabela muito simples na qual temos o ID do
usuário, o ID do jogo e o registro de data e hora do jogo.
Com essa tabela, podemos fazer consultas com base no ID do usuário.
Portanto, ele me fornece todos os jogos desse usuário,
mas não podemos consultar o ID do jogo, como podemos ver agora. Se
você quiser consultar o ID do
jogo, será extremamente difícil fazer uma varredura
e filtrar o site do cliente.
Portanto, em vez disso, vamos criar um GSI,
um índice secundário global.
O que nos dará a capacidade de consultar por ID de jogo.
Portanto, agora a chave de partição do GSI se torna a ID do jogo.
A chave de classificação pode ser, por exemplo, o registro de data e hora do jogo.
É sobre isso que você deseja consultar.
E os atributos se tornam ID de usuário porque fizemos
uma projeção dos atributos de ID de usuário.
Portanto, você pode ver que, neste caso, estamos criando algumas
novas consultas totalmente diferentes, definindo uma nova
chave de partição e uma chave de classificação.
E é por isso que é muito importante
que o DynamoDB entenda como você
vai consultar os dados, como
vai criar seus índices secundários
locais e seus índices secundários globais.
Portanto, vimos que o LSI e o GSI têm finalidades muito, muito diferentes,
mas vamos falar sobre esses índices e a limitação.
Portanto, quando você tiver um
GSI, se os direitos forem uma ameaça à carga no GSI,
a tabela principal também será fértil.
Portanto, essa é uma advertência muito, muito
importante que aparece no exame.
Portanto, mesmo que as WCUs estejam bem na tabela principal, se houver estrangulamento
na GSI, na tabela principal, não importa o que aconteça, haverá
estrangulamento e, portanto,
escolha cuidadosamente a GSI e a chave parcial e atribua a capacidade
da WCU com muito, muito cuidado.
Já para os índices secundários locais
(LSI), eles usarão a WCU e a RCU da tabela principal.
E não há considerações especiais de limitação de velocidade a serem feitas.
Está bem?
Então é isso para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
