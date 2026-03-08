esteja no exame, acho que
aparecerá muito em breve. Para mim, o Kinesis Enhance Fan Out é o que chamo de recurso
revolucionário, e ele foi lançado em agosto de 2018. Portanto, tenho certeza de que ele estará no exame muito
em breve.
Então, como podemos aproveitar isso?
Bem, isso funcionará se você usar o KCL 2. 0 ou AWS lambda a partir de novembro de 2018. portanto, ele é apoiado por esses dois
fatores.
E o que significa Enhance FanOut, que significa que cada consumidor terá dois megabytes por segundo por fragmento.
Portanto, a aparência é semelhante à anterior, mas não é exatamente a mesma, certo?
Portanto, temos um produtor que produz fluxos de dados do Kinesis e tem, por exemplo, um fragmento neste exemplo.
Teremos um aplicativo de consumidor a.
E ele fará uma chamada de API para assinar o fragmento e poderá usar automaticamente o fluxo de dados.
Começaremos a enviar dados, a uma taxa de dois megabytes por segundo, de modo que não estaremos mais puxando.
Estamos apenas dizendo para se inscrever no shard. E a Lasca nos enviará dois megabytes por segundo.
Isso significa que, se tivermos 20 consumidores, obteremos 40 megabytes por segundo, por fragmento.
Assim, podemos começar a adicionar aplicativos para consumidores.
Faça a chamada do assinante novamente e obtenha mais dois megabytes por segundo.
Portanto, antes tínhamos um limite de dois megabytes por segundo por fragmento, mas agora temos dois megabytes por
segundo por limites por fragmento e por consumidor.
O motivo é que o Enhance FanOut tem o Kinesis enviando dados aos consumidores por HTTP/2.
E o benefício adicional disso é que, em primeiro lugar, podemos dimensionar muito mais aplicativos de consumo.
E a outra é que temos uma latência reduzida.
Portanto, antes de lembrar, tínhamos essa latência de 200 milissegundos caso tivéssemos um consumidor, porque
ele podia puxar cinco vezes por segundo. E, na verdade, se tivéssemos mais consumidores, todos eles acrescentariam
uma latência de um segundo. Bem, com o ventilador aprimorado agora,
temos uma latência reduzida, porque os dados são enviados para nós. E, em média, você terá uma latência de 70 milissegundos, o
que é muito menos do que 200 milissegundos ou um segundo.
Portanto, o Enhance FanOut é, para mim, um recurso revolucionário e fico feliz em dizer que ele existe.
Obviamente, você terá que pagar um pouco mais por isso e a página de preços da AWS o ajudará a entender quanto
terá que pagar por isso.
Qual é a diferença entre o FanOut aprimorado e os padrões do consumidor?
E quando você usaria cada uma delas? Portanto, um consumidor padrão será usado quando você
tiver um número baixo de aplicativos de consumo, digamos, um, dois ou três, e puder tolerar alguma latência
de duzentos milissegundos ou mais, e quiser minimizar o custo, pois esse consumidor centrado no cliente
já está incluído nos casos, e você usará consumidores fan out aprimorados se quiser ter vários aplicativos
consumindo o mesmo fluxo, estamos falando de cinco ou 10 aplicativos ao mesmo tempo, e quiser
requisitos de latência muito baixos, de modo que talvez só possa tolerar requisitos de latência de 70 milissegundos e, obviamente,
isso trará um custo mais alto, como eu disse, veja a página de preços do Kinesis para isso e, por padrão, quando
você usa o consumidor fan out, há um limite de 20 consumidores que podem usar o fan out, mas você pode aumentar
isso fazendo uma solicitação de serviço no suporte da AWS.
Espero que isso faça sentido.
Espero que você esteja animado com esse novo recurso.
Sinceramente, é incrível e tenho certeza de que o exame lhe perguntará sobre isso muito em breve, então é
bom aprender sobre isso.
Para mim, isso muda o jogo porque agora podemos ter 20 consumidores em um fragmento e não ter
nenhum impacto em cada um deles, o que, para mim, é realmente uma mudança de jogo.
Tudo bem, já falei o suficiente. Vejo vocês na próxima palestra.
