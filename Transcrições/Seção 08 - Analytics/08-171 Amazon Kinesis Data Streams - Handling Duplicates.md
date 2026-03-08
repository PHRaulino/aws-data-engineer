Agora vamos
Streams e há dois casos em que isso pode acontecer.
Há no lado do produtor e também
no lado do consumidor.
Portanto, as novas tentativas do produtor podem criar duplicatas
devido principalmente aos tempos limite da rede, e essa é uma pergunta de exame.
Então, como isso funciona?
Bem, você tem seus produtores, que podem ser
aplicativos, podem estar usando o SDK ou o KPL
e estão produzindo em um fluxo de dados do Kinesis.
Agora, quando fazemos um PutRecord e enviamos alguns dados, sabemos
o que acontece.
Os dados são gravados no fluxo de dados do Kinesis,
recebem um número de sequência exclusivo e, em seguida,
o fluxo de dados do Kinesis diz: "Retornei
seus dados corretamente. Mas, no caso de um tempo
limite da rede, essa confirmação pode nunca chegar ao nosso
aplicativo produtor.
Pode ser devido a um tempo limite da rede e nosso
produtor não pode saber disso, então talvez ele diga: "Ok, acho que
esse registro não foi escrito porque
não recebi nenhuma confirmação de retorno". E agora há um tempo
limite.
Portanto, o que vai
acontecer é que o registro do produtor será tentado novamente
pelo nosso aplicativo, reemitindo uma chamada de API.
Então, vamos fazer um PutRecord novamente para os mesmos
dados, que serão gravados uma segunda
vez no meu fluxo de dados e, como você
pode ver, o número de sequência aumentou de 123 para 124, e agora as confirmações,
que estão de volta ao nosso produtor, estão
prontas para serem usadas.
Mas o que aconteceu é que,
do ponto de vista do Kinesis Data Stream, criamos
registros duplicados porque os
mesmos dados foram gravados duas vezes e receberam
dois IDs de sequência diferentes.
Assim, embora os dois registros tenham dados idênticos,
eles também têm números de sequência exclusivos
e, portanto, haverá dois pontos de dados
em nosso Kinesis Data Stream.
Portanto, a solução para isso é incorporar um ID de registro exclusivo
nos dados para poder fazer a deduplicação com base nesse
ID de registro exclusivo no lado do consumidor.
Portanto, isso, embora pareça assustador,
eu diria que raramente acontece, mas ainda assim
é um caso usado, é um caso que você deve
conhecer e sobre o qual o exame o testará.
Agora vamos falar sobre o que pode acontecer
no lado do consumidor com relação às duplicatas.
Portanto, as novas tentativas do consumidor podem fazer
com que o aplicativo leia os mesmos dados duas vezes, e as novas tentativas do consumidor
podem ocorrer em quatro tipos diferentes de casos
de uso, mas todos eles correspondem a quando
o processador de registros será reiniciado.
Portanto, pode ser quando um trabalhador termina inesperadamente,
pode ser quando as instâncias de um trabalhador são adicionadas ou removidas,
pode ser quando os fragmentos são mesclados ou divididos ou
quando o aplicativo é implantado.
Portanto, lembre-se desses quatro casos, pois
eles também podem aparecer no exame.
Portanto, a correção para isso é bastante difícil
e a documentação é bastante vaga, mas a ideia é que você torne
o aplicativo do consumidor idempotente.
Isso significa que, se você ler os mesmos dados duas
vezes, eles não terão os mesmos efeitos colaterais duas vezes.
E a outra recomendação fornecida pela
documentação do AWS é que, se de alguma forma
seu destino final puder lidar com duplicatas, é recomendável
fazer isso lá.
Por exemplo, se você puder contar com esse ID de registro exclusivo e inseri-lo
em um banco de dados, o banco de dados não
permitirá que você insira esse ID de registro exclusivo
duas vezes e, portanto, essa
pode ser uma boa opção para você.
Se quiser obter mais informações,
leia a documentação aqui,
mas, do ponto de vista do exame, você precisa
saber que os tempos limite da rede podem introduzir
duplicatas do lado do produtor e que essas
quatro tentativas do consumidor podem
introduzir duplicatas do ponto de vista do consumidor, pois os
dados serão lidos duas vezes.
Então é isso para esta palestra.
Espero que tenham gostado
e nos veremos na próxima palestra.
