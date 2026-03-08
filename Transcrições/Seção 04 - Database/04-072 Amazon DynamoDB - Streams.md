Então, vamos dar uma olhada nos fluxos do DynamoDB.
Portanto, os fluxos são uma lista ordenada de modificações em nível de item, como
criação, atualização e exclusão, que estão
ocorrendo em uma tabela.
Portanto, sempre que você inserir
um item, modificá-lo ou excluí-lo,
E o fluxo representará a lista
de todas as modificações ao longo do tempo em sua tabela.
Assim, os registros de fluxo podem ser enviados para vários
locais, como os fluxos de dados do Kinesis,
para que você possa enviar um fluxo do DynamoDB para
o Kinesis e depois fazer o que quiser com ele.
Você também pode usar uma função Lambda
para ler diretamente de seus fluxos do DynamoDB ou
pode usar os aplicativos da biblioteca de clientes
do Kinesis para ler diretamente também de um fluxo do DynamoDB.
A retenção de dados em um DynamoDB Stream
é de até 24 horas, portanto,
você precisa persistir
em algum lugar como o Kinesis Data Stream, onde
é possível ter uma retenção mais
longa, ou usar qualquer aplicativo Lambda ou KCL para persistir em algum
lugar mais durável.
Os casos de uso do DynamoDB Streams são
para reagir às mudanças em tempo real que
ocorrem nas tabelas do DynamoDB.
Por exemplo, ter um fluxo para dar as boas-vindas
a você, enviar um e-mail de boas-vindas aos seus
usuários, fazer análises,
transformar o fluxo e criar tabelas derivadas
no DynamoDB ou enviar dados para o OpenSearch para indexação e fornecer recursos
de pesquisa sobre o DynamoDB.
Ou, se você quisesse implementar tabelas
globais e replicação entre regiões,
precisaria ter fluxos em primeiro lugar.
Portanto, se observarmos a arquitetura dos fluxos do
DynamoDB, teremos nosso aplicativo,
que realiza operações de criação,
atualização e exclusão em nossa tabela, e qualquer uma
dessas alterações aparecerá em um fluxo do DynamoDB.
Portanto, a partir daí, o Kinesis Data Streams pode ser um receptor
de seu fluxo do DynamoDB.
E como estamos usando o KDS, Kinesis
Data Streams, podemos ter o Kinesis Data Firehose
como resultado e, em seguida, talvez enviá-lo para
o Amazon Redshift para realizar
algumas consultas analíticas sobre os dados no DynamoDB,
ou enviá-lo para o Amazon S3 para
arquivar todas essas alterações, caso seja necessário,
ou enviá-lo para o OpenSearch Service, ok, para indexá-lo e
criar um recurso de pesquisa sobre a tabela
do DynamoDB.
O interessante dessa arquitetura
é que praticamente tudo é gerenciado pelo AWS.
Se você quisesse adicionar sua própria lógica personalizada,
poderia usar uma camada de processamento na qual criaria
um aplicativo da biblioteca de clientes do Kinesis,
talvez em execução no EC2, ou
uma função Lambda que estaria lendo os
fluxos do DynamoDB.
E, a partir disso, você pode implementar qualquer tipo de lógica que desejar.
Assim, por exemplo, você pode enviar mensagens
ou notificações usando o Amazon SNS.
Você pode fazer algumas filtragens e transformações
e, em seguida, reinserir os dados em uma tabela do DynamoDB ou, por
exemplo, também pode usar o Lambda para enviar dados para o
OpenSearch, se quiser, certo?
Portanto, isso oferece a você diferentes
tipos de arquiteturas e todas as possibilidades que
se abrem com o uso do DynamoDB Streams.
Então, se considerarmos o fluxo, o que temos?
No fluxo, temos a
capacidade de escolher as informações
que serão exibidas nele.
Assim, podemos, por exemplo, ter apenas
as chaves, e ele mostrará apenas uma lista
de todos os atributos-chave que foram modificados,
NEW_IMAGE, que representa o novo item depois
de modificado, OLD_IMAGE, que representa o item inteiro como aparece
antes de ser modificado.
E se quiser obter as informações
completas, você pode obter NEW_AND_OLD_IMAGES,
que fornece a imagem nova e a antiga do item e, portanto,
podemos ver quais mudanças ocorreram.
Agora, os fluxos do DynamoDB são feitos de fragmentos, assim como os fluxos
de dados do Kinesis, portanto, são muito,
muito semelhantes.
E é por isso que a biblioteca de clientes do Kinesis funciona
tanto com os fluxos do DynamoDB quanto com
os fluxos de dados do Kinesis.
O interessante do DynamoDB Streams é que não precisamos
provisionar nenhum tipo de fragmento.
Isso é feito automaticamente pela AWS, portanto,
é realmente uma abordagem sem intervenção.
Agora, se você habilitar o DynamoDB Stream, para que você saiba,
os registros não serão preenchidos retroativamente no
stream depois de habilitá-lo.
Muito bem, este é um truque para o exame.
Portanto, depois de
ativar o fluxo, só então você receberá essas atualizações
com base nas alterações que estão aparecendo
na tabela do DynamoDB.
Por fim, vamos dar uma olhada
em como funcionam o DynamoDB Streams e o Lambda.
Portanto, para isso, precisamos definir um mapeamento de fonte
de eventos para ler de um fluxo do DynamoDB.
E, em seguida, você precisa garantir que
a função Lambda tenha as permissões
adequadas para extrair do fluxo do DynamoDB.
E então a função Lambda será chamada de forma síncrona.
Então, vamos dar um exemplo.
A tabela vai para um DynamoDB Stream.
A função Lambda terá um mapeamento de fonte
de eventos, que é um
processo interno que puxará o fluxo do DynamoDB
e recuperará registros em lotes do fluxo
do DynamoDB.
E quando alguns registros forem passados
para o Event Source Mapping,
o Event Source Mapping invocará
suas funções Lambda de forma síncrona com
um lote de registros do seu DynamoDB Stream, certo?
Então é isso para esta palestra.
Espero que você tenha gostado
e nos vemos na próxima palestra para um pouco de prática.
