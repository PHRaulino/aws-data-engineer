para a minha fila de demonstração.
Portanto, chamarei este de DemoQueueDLQ.
Vou rolar a tela para baixo e, como se trata de uma fila de cartas
mortas, quero me dar tempo suficiente para
reter e analisar as mensagens.
Portanto, terei um período de retenção de mensagens de 14 dias.
Certo, perfeito.
Então, vamos rolar a tela para baixo.
Teremos uma criptografia padrão ativada.
Tudo parece bem aqui
e vamos criar essa fila.
Agora que essa fila foi criada com sucesso,
vamos abrir uma nova guia e acessar a configuração
da minha DemoQueue.
Então, aqui, vou editar a fila em si e o tempo limite de visibilidade
será definido como algo muito
lento, muito baixo, desculpe, para
ser um pouco mais rápido em minha demonstração.
Portanto, teremos cinco segundos
para ler as mensagens três vezes muito rapidamente.
Se eu rolar a tela para baixo em Dead-letter
queue (Fila de cartas mortas),
poderei habilitá-la e escolher DemoQueueDLQ como QSQ como minha fila de cartas
mortas.
Agora precisamos especificar o recebimento máximo.
Portanto, essa é a quantidade de vezes que a mensagem
deve ser recebida antes de ser colocada no DLQ.
E para sermos um pouco mais rápidos, estamos dizendo três.
Portanto, depois que a mensagem
for lida três vezes e colocada de volta
na fila uma quarta vez, ela acabará em meu SQS DLQ.
Então, vamos salvar isso e pronto.
Então, agora vou para o meu DLQ e começarei
a receber mensagens e a pesquisar mensagens.
E, neste momento,
é claro, não temos nenhuma mensagem
em meu DLQ, mas vamos para minha fila normal
agora e enviarei e receberei mensagens.
E este vai ser
"hello world, poison pill".
Pílula venenosa, porque, na verdade,
ela fará com que meu aplicativo de consumidor fracasse.
Por isso é chamada de pílula de
veneno, mas não temos nenhum aplicativo para o consumidor.
Esse é apenas um aplicativo de consumidor.
Portanto, vamos enviar a mensagem.
A mensagem foi enviada.
E agora vamos fazer uma pesquisa de mensagens.
Portanto, aqui estamos recebendo as mensagens
uma vez e, após cinco segundos, as receberemos uma segunda vez.
E depois de, novamente, cinco segundos,
receberemos uma terceira vez, como você
pode ver aqui.
E depois que a mensagem for recebida três vezes, bem, como
ela está sempre sendo colocada de volta na
fila, ela não está sendo descartada,
então a mensagem será enviada para o DLQ.
Então, vamos verificar isso.
Agora, se eu parar de sondar agora e tentar sondar
novamente para receber novas mensagens, verei
que não receberei mais a mensagem.
Então, para onde foi a mensagem?
Bem, se entrarmos no próprio DLQ, este
é o meu DLQ, e eu pesquiso mensagens,
como você pode ver, vejo
a mensagem no meu DLQ agora.
E essa mensagem, se eu clicar nela como meu DLQ,
poderei dizer: "Ok, dei uma olhada nessa
mensagem e é por causa dela que meu aplicativo principal travou. Por fim, vou lhe mostrar como redirecionar essa
mensagem do DLQ para essa
primeira fila.
No caso, por exemplo, de consertarmos nosso aplicativo de consumidor.
Portanto, no meu DLQ, vou até aqui e,
no canto superior
direito, há um redrive Start DLQ.
Portanto, estamos dizendo: "Ei, este é um DLQ e você
recebeu mensagens. Portanto, você deseja
redirecionar essas mensagens para
a fila de origem.
Então, basta clicar nessa opção.
Para o controle de velocidade, teremos o Systemoptimized,
e então poderemos inspecionar as mensagens, se quisermos.
Em seguida, basta clicar em DLQ redrive.
Por isso, ela é chamada de tarefa de redrive DLQ.
E se eu for até aqui, verei
que ela já foi concluída com sucesso.
Isso significa que, se eu voltar para a minha DemoQueue,
a fila de origem, e entrar
em Enviar e receber mensagens e pesquisar mensagens,
como você pode ver,
a mensagem reaparecerá bem aqui.
Portanto, o redrive funcionou.
Esperamos que isso lhe dê uma boa visão geral
de como funcionam as filas de letras mortas.
Espero que tenham gostado
e nos veremos na próxima palestra.
