Agora, como o DynamoDB se relaciona
com o mundo do big data?
Bem, há alguns casos de uso muito comuns,
que incluem aplicativos móveis, jogos, anúncios
digitais na veiculação, votação ao vivo, interação com o público
em eventos ao vivo, rede de sensores,
ingestão de logs, controle de acesso para conteúdo baseado
na Web, armazenamento de metadados para objetos
do Amazon S3, carrinho de compras de comércio eletrônico,
gerenciamento de sessões da Web.
Portanto, os casos de uso são bastante diversos,
mas basicamente isso significa que, sempre que
você tiver dados que precisem ser muito quentes, que precisem
ser ingeridos em escala em um banco de
Em termos de antipadrão, o que você não faz com um DynamoDB?
Bem, por exemplo, um aplicativo que usa o RDS como um
banco de dados tradicional, como um RDBMS,
então você não usa o RDS porque
não quer reescrevê-lo completamente.
Ou, se você precisar fazer junções ou transações complexas, o DynamoDB
talvez não seja o melhor amigo para isso.
Talvez, mais uma vez, um banco de dados RDS seja melhor para você.
Se você precisar armazenar Binary Large Objects ou dados BLOB.
Portanto, talvez seja melhor armazenar
big data no S3 e instalar os metadados
no DynamoDB.
Esse é um padrão muito comum.
E, em geral, se você tiver dados grandes com baixas
taxas de E/S, ou seja, taxas
muito baixas ou leituras muito baixas, o S3 será uma opção
de armazenamento muito melhor para você.
Então, pense nisso.
O DynamoDB será mais adequado para quando
seus dados forem quentes e menores.
Por outro lado, o S3 será mais caro quando seus dados
forem um pouco mais frios, mas muito maiores.
