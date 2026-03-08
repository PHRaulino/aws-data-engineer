Agora vamos
A ideia é que vamos entrar no cenário em
que um consumidor não consegue processar uma mensagem
dentro do período de tempo limite de visibilidade.
Então, sabemos que a mensagem
volta automaticamente para a fila.
Então o consumidor lê a mensagem,
talvez haja uma falha, talvez
não tenhamos tempo suficiente.
A mensagem volta para a fila.
Agora, se isso acontecer com muita frequência,
pode ser um problema.
Por exemplo, se lermos novamente
a mensagem, talvez haja algo errado com a mensagem.
Talvez nosso consumidor não entenda a mensagem
ou não consiga processá-la.
Em seguida, a mensagem voltará para a fila e isso ocorrerá
novamente.
Leremos a mensagem novamente
do SQS e ela voltará para a fila.
Portanto, podemos definir um limite
para o número de vezes que isso pode acontecer.
E esse loop de falha
pode ser um grande problema,
mas podemos definir um limite de MaximumReceives.
E se esse limite for ultrapassado, podemos dizer
ao SQS para dizer: "Bem, essa
mensagem parece um pouco estranha.
Parece que ele está sendo processado muitas
vezes e sem sucesso. Portanto, envie
isso para uma fila de cartas mortas.
E a fila de cartas mortas conterá essa mensagem para processamento
posterior.
Assim, a mensagem será removida
da primeira fila e enviada para a segunda.
Por que temos filas de espera para cartas mortas?
Bem, as filas de letras mortas são muito úteis para depuração e, caso
uma mensagem vá para a fila de letras mortas por ser uma fila
SQS, você terá que processá-la, mas pelo menos
isso lhe dará tempo
para entender o que está acontecendo.
Alguns aspectos a serem observados
são que a fila de cartas mortas de uma fila FIFO também
deve ser uma fila FIFO, e a fila de cartas mortas
da fila padrão também deve ser uma fila padrão.
Por fim, como temos uma fila de cartas mortas,
você precisa garantir que as mensagens sejam processadas antes
de expirarem da
fila.
Portanto, é uma boa ideia definir
um longo período, por exemplo, 14
dias de retenção
na fila de cartas mortas.
E o próximo recurso para o gerenciamento
de suas filas de cartas mortas é o recurso de redirecionamento
para a origem.
Portanto, é um recurso que o ajuda a consumir mensagens
na fila de cartas mortas para entender o que há de errado com elas.
Portanto, agora você tem
suas mensagens e sabe que elas não foram processadas
na fila de origem e, portanto, estão na fila
de cartas mortas, e você fará uma inspeção manual
e a depuração dessas mensagens.
E então você corrigirá seu código de consumidor
para entender por que a mensagem não foi processada,
caso a mensagem estivesse correta.
E o que você pode fazer é redirecionar a mensagem
da fila de cartas mortas para a fila SQS de origem. E o que acontecerá
com isso é que o consumidor poderá
reprocessar a mensagem sem nem mesmo saber que ela foi
para a fila de cartas mortas e que o
processamento da mensagem
já ocorreu, o que é um recurso interessante.
Então, agora vamos para o console
para que eu possa mostrar o recurso Dead Letter Queue.
