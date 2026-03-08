maneiras de usar o DynamoDB com o Amazon S3.
A primeira é como armazenar
objetos grandes no DynamoDB.
Bem, acontece que, como você sabe,
em suas tabelas no DynamoDB, você só pode
armazenar até 400 kilobytes de dados.
Então, obviamente, se você quiser começar a armazenar algumas
imagens, alguns vídeos, todo esse tipo
de coisa, o DynamoDB não é o melhor lugar para isso.
Portanto, em vez disso, o que faremos
é ter um bucket do Amazon S3 que conterá nossos objetos
grandes.
Então, qual é o processo para fazer upload de um objeto grande?
Bem, digamos que carregamos uma imagem
no Amazon S3.
Vamos recuperar a chave dos objetos.
E o que vamos fazer é armazenar
esses metadados
do aplicativo no DynamoDB.
Portanto, teremos um ID de produto,
um nome de produto e um URL de
imagem, que é um ponteiro diretamente
para o Amazon S3.
Agora, o que fizemos
foi armazenar efetivamente uma quantidade muito pequena
de dados em nossa tabela de produtos
no DynamoDB.
E armazenamos o item grande no Amazon S3.
Agora, do ponto de vista da leitura
e dos clientes que desejam ler esses
dados, primeiro obtemos os metadados do dynamo
DB e, em seguida, obtemos a imagem de volta do Amazon S3 para
reconstruir esses objetos grandes.
Portanto, podemos continuar e ter muitos produtos diferentes e usar a estratégia
em escala.
E o que é legal nessa estratégia é que estamos usando cada serviço
para aquilo em que ele é bom.
Portanto, o Amazon S3 é excelente para armazenar objetos grandes.
Está bem.
E o DynamoDB é ótimo para armazenar pequenos
objetos que serão indexados com atributos específicos.
Portanto, neste
exemplo, temos a combinação perfeita do Amazon S3 e do DynamoDB.
Outra combinação ou sinergia
que podemos ter é usar o DynamoDB como uma forma
de indexar os metadados dos objetos do S3.
Portanto, o aplicativo fará upload de objetos para o Amazon S3 e, no Amazon
S3, teremos notificações configuradas, por
exemplo, para invocar uma função Lambda.
Essa função Lambda armazenará
os metadados dos objetos na tabela do DynamoDB, por exemplo,
tamanho do objeto, data, quem o criou, o
que você quiser pensar sobre esses objetos.
Bem, porque é muito
mais fácil para nós criar algumas consultas sobre
a tabela do DynamoDB.
Em seguida, em cima de um bucket S3, novamente, um bucket S3 não
se destina a ser realmente escaneado.
Ele foi criado para armazenar objetos grandes e, supostamente, você
deve ter algum tipo de banco de dados que saiba quais
são esses objetos, seus atributos e assim por diante.
Portanto, ao criar um aplicativo sobre o DynamoDB, podemos responder
a algumas perguntas, como: "Queremos que você
encontre objetos por um registro de data e hora específico em nossos buckets
do S3".
Ou queremos encontrar o armazenamento total usado por um cliente ou listar
todos os objetos por atributos ou encontrar todos os objetos
do S3 carregados em um intervalo de datas, embora isso seja feito por meio de
consulta à tabela do DynamoDB.
Em seguida, lemos de volta os resultados do DynamoDB
e recuperamos os objetos necessários de seus buckets do S3.
Está bem.
Portanto, esperamos que essas duas estratégias façam sentido.
Elas são bastante comuns e podem aparecer no exame.
Espero que você tenha gostado.
E eu o verei na próxima palestra.
