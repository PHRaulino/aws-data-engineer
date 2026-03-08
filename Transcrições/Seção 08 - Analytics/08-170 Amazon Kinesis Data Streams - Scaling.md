importante entender como você pode dimensionar
o Kinesis.
Portanto, a primeira operação que você pode fazer é adicionar
fragmentos, e adicionar fragmentos no mundo Kinesis é chamado de Shard Splitting (divisão de fragmentos),
e veremos o porquê em um segundo momento.
Ele pode ser usado para, basicamente, aumentar a capacidade do fluxo.
Então, lembre-se de como você obtém um megabyte por
segundo, por dados, por fragmento, e se você tiver 10 fragmentos, terá 10 megabytes,
certo.
Portanto, se você quiser aumentar a capacidade
do fluxo, precisará dividir um fragmento.
Também pode ajudar a usar e dividir um fragmento quente.
Portanto, se você tiver um fragmento quente, um fragmento
que está sendo mais usado do que outros, nós o dividiremos
e isso provavelmente aumentará nossas taxas de transferência.
Então, o que acontece quando você divide um fragmento?
Bem, o fragmento antigo está
fechado e será excluído quando os dados nele contidos expirarem.
Então, vamos dar uma olhada em um diagrama,
pois acho que ele fará muito mais sentido.
Portanto, temos os fragmentos um, dois e três, neste
exemplo, e eles ocupam o mesmo espaço.
Agora, o fragmento dois está muito quente e queremos
dividi-lo para aumentar as taxas de transferência
nesse espaço-chave do fragmento dois.
Portanto, faremos uma operação de divisão,
e o que acontecerá é que haverá o fragmento
quatro, que foi criado, e o fragmento cinco,
que está sendo criado.
E, como você pode ver, eles estão ocupando o
mesmo espaço que o fragmento dois, mas agora, como
temos dois fragmentos, temos
dois megabytes por segundo nesse espaço, em
vez de um megabyte por segundo.
Os outros fragmentos, um e três, permanecem os mesmos.
Portanto, antes de nosso fragmento se parecer com este, ele tem três fragmentos, nosso fluxo
se parece com este, ele tem três fragmentos
e, depois que ele se divide, temos quatro fragmentos e
podemos ver que quatro e cinco
estão ocupando o espaço do fragmento dois.
Portanto, o fragmento dois estará disponível enquanto os dados nele
contidos não tiverem expirado, mas quando expirarem, ele desaparecerá.
Portanto, este é o estado do nosso novo fluxo do Kinesis.
Quando os produtores gravam dados nele,
eles têm quatro fragmentos para gravar.
Portanto, é muito importante entender esse conceito,
porque, basicamente, você pode dividir quantos fragmentos
quiser, ao longo do tempo,
e aumentar sua taxa de transferência dessa forma.
Agora, qual é a operação inversa à adição
ou divisão em fragmentos?
Bem, é diminuir os fragmentos ou mesclar fragmentos.
Assim, ao mesclar fragmentos, você usaria
isso para diminuir a capacidade do fluxo e economizar alguns custos.
E pode ser usado, por exemplo,
para agrupar dois fragmentos que têm pouco tráfego
e você deseja mesclá-los para economizar custos.
Portanto, os fragmentos antigos serão fechados e excluídos,
novamente, com base na expiração dos dados.
Então, agora, por exemplo, digamos que temos esse
fragmento e ele tem nosso fluxo, e tem um, quatro
e cinco, e três, exatamente como
antes, e queremos mesclar um e quatro juntos.
Então, vamos mesclá-los e ele está se tornando
o fragmento seis, porque, talvez, os fragmentos um e
quatro não tenham recebido muito tráfego,
então podemos mesclá-los e economizar algum custo.
Então, nós os mesclamos e, em seguida, os fragmentos cinco e três,
embora eles permaneçam como antes, e agora passamos de quatro
fragmentos para três fragmentos em nosso novo fluxo,
porque o mesclamos.
Portanto, como você pode ver, agora podemos mesclar e dividir,
mesclar e dividir, e podemos, basicamente,
modular todo o nosso fluxo de dados do Kinesis para aumentar e diminuir
as taxas de transferência ao longo do tempo.
É assim que funciona.
Instrutor 2: Uma pergunta de cenário comum
no exame o questionará sobre um caso em que o produtor
está enviando dados para um fluxo do
Kinesis com a chave de partição correta,
mas o consumidor recebeu os dados fora de ordem
em algum momento.
Portanto, um motivo para isso seria o resharding.
Vamos explorar esse caso de uso.
Portanto, quando você faz um resharding de Kinesis,
pode lê-lo diretamente dos fragmentos filhos
após o resharding.
No entanto, se você ainda não leu todos os
dados do fragmento pai, então
o que acontecerá é que você poderá ler os dados fora
de ordem para uma determinada chave de hash.
Então, vamos dar uma olhada em um diagrama.
Portanto, temos a acelga principal
e temos um dispositivo produzindo para considerar o fluxo
usando o KPL, por exemplo.
E temos um aplicativo de consumidor
em execução no EC2, usando o SDK.
Portanto, vamos fazer chamadas à API GetRecords.
Então, digamos que esse seja o dispositivo IoT logo antes
de uma operação de resharding enviar alguns dados, um e dois.
Portanto, em termos de
taxas de consumo, nosso aplicativo de consumo
tem consumido tudo no fragmento pai até os dois pontos de dados, um e dois.
Em seguida, iniciamos uma operação de divisão de fragmentos.
Portanto, a partir desse
fragmento pai, teremos dois novos fragmentos filhos, e o que acontecerá
é que, quando essa divisão terminar, o dispositivo IoT
começará a produzir para o novo fragmento filho, porque
o fragmento pai será fechado
para direitos.
Isso significa que os pontos de dados, três
e quatro, acabarão no fragmento filho.
Agora, se o aplicativo do consumidor não for muito, muito inteligente,
o que acontecerá é que você poderá solicitar dados diretamente
do fragmento filho antes de ler o final
dos pais.
Isso significa que você verá
os pontos de dados três e quatro primeiro e, talvez, um e dois em seguida.
Portanto, isso é algo que pode criar registros fora de ordem,
registros fora de ordem, desculpe, depois de uma operação de resharding.
Portanto, a diretriz é que, após um reshard, na lógica do
aplicativo do consumidor, você precisa
ter certeza de que tem a lógica
para ler inteiramente do pai até que não haja
novos registros do pai.
Isso significa que você chegou ao final
do fragmento pai e, em seguida, pode começar a ler no fragmento
filho, o que garantirá a ordem dos registros.
Isso pode ser complicado de implementar,
portanto, como observação, a biblioteca de clientes do Kinesis, a KCL,
já tem essa lógica incorporada, mesmo após a operação de
reescalonamento, portanto, você está pronto para começar.
Mas esperamos que você esteja bem com esse caso
de uso, e isso pode aparecer no exame.
Instrutor 1: E quanto ao Auto Scaling, você pode dizer,
temos que fazer essas coisas manualmente?
Bem, existe o Auto Scaling, mas não
é um recurso nativo do Kinesis, e há uma chamada de API
que você pode usar para atualizar a contagem de fragmentos
chamada UpdateShardCount, e você pode implementar
algum tipo de Auto Scaling usando o AWS Lambda.
Há um blog inteiro sobre isso, caso esteja
curioso, e este é o diagrama de arquitetura diretamente desse blog.
Portanto, leia esse blog se você
estiver interessado em implementar
o Auto Scaling, mas terá que fazer isso manualmente para que funcione.
E então, você pode usar o Scaling?
Quais são suas limitações?
Bem, não é possível fazer um resharding em paralelo, portanto,
é necessário planejar a capacidade com antecedência.
Isso significa que você não pode, por exemplo, fazer o resharding de mil fluxos
de uma vez ou de mil fragmentos de uma vez, pois isso
não funcionaria. Portanto, é aqui que você precisa planejar
a capacidade com bastante antecedência, caso
esteja esperando grandes taxas de transferência, e você só pode executar uma operação de
resharding por vez, o que leva alguns segundos.
Portanto, por exemplo, se você tiver 1.000 fragmentos,
levará cerca de 30.000 segundos, ou 8. 3 horas, para dobrar
o número de fragmentos até 2000.
Isso lhe dá uma ideia de que o dimensionamento,
no Kinesis, não é instantâneo, leva tempo.
E, como você pode ver, dobrar de 1.000 fragmentos
para 2.000 fragmentos leva mais de oito horas, portanto,
precisamos planejar com bastante antecedência.
Além disso, há algumas limitações.
Elas são um pouco complexas,
e você não precisa se lembrar delas,
mas acrescentei esses slides
para o caso de você precisar usar o Kinesis no mundo real
e precisar conhecê-las.
Portanto, aqui estão todos eles.
Basicamente, isso significa que você não pode aumentar a escala muito rapidamente
e não pode diminuir a escala muito rapidamente.
Há alguns limites que a AWS impõe a você.
Portanto, não vou lê-los para você,
você não precisa conhecê-los para o exame, tudo bem,
só precisa saber que o resharding em escala não pode
ser feito em paralelo e que você precisa, basicamente, fazer
o resharding leva alguns segundos para cada fragmento,
portanto, lembre-se de que, para mil fragmentos,
leva cerca de 8. 3 horas para dobrar o número
de fragmentos para 2000.
É disso que quero que você se lembre.
Não é necessário lembrar de todas as limitações, obviamente, mas elas
estão aqui apenas como referência, caso você
precise delas para sua aplicação no mundo real.
Muito bem, então é isso para o Kinesis Scaling,
espero que você tenha gostado e nos vemos na próxima palestra.
