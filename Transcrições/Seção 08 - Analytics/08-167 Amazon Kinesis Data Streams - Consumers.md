consumir dados do Kinesis Data Streams.
Primeiro, falaremos sobre os consumidores clássicos.
Portanto, o primeiro é o Kinesis SDK.
Da mesma forma, poderíamos usar uma CLI
ou alguma linguagem de programação.
Para enviar dados por meio dos fluxos de dados
do Kinesis, podemos usar o SDK ou a CLI para ler dados
dos fluxos de dados do Kinesis.
Também podemos usar a biblioteca de clientes Kinesis, e eu dei uma
dica sobre isso na palestra anterior.
Seu nome é KCL.
Portanto, produzimos com o KPL e lemos com o KCL.
Há também a Kinesis Connector Library, que poderia
ser abreviada como KCL, mas na verdade não é.
Portanto, é um pouco diferente da Consumer Client Library.
Além disso, temos bibliotecas de
terceiros, como Apache Spark, Log4j, Flume, Kafka Connect,
todas essas coisas.
Mas o exame espera que você saiba que o Apache
Spark é capaz de ler os fluxos de dados do Kinesis como um consumidor.
Também podemos usar o Kinesis
Data Firehose e o AWS Lambda, se necessário.
Há um mecanismo de consumo chamado Kinesis
Consumer Enhanced Fan-Out, que discutirei na
próxima palestra.
Portanto, por enquanto, vamos considerar apenas como um consumidor clássico
funcionaria no Kinesis.
Então, primeiro, o SDK.
Obter registros.
Portanto, este é o Kinesis clássico,
o que significa que os registros serão pesquisados
ou agrupados pelo consumidor a partir de um fragmento.
E cada fragmento terá um total máximo de dois megabytes
de throughput agregado.
Portanto, cada fragmento, lembre-se, é um megabyte de
produtor, dois megabytes de consumidor.
Então, aqui está o exemplo.
Nosso produtor está produzindo dois Kinesis Data Stream,
e ele é formado talvez por, digamos, três fragmentos.
Portanto, se tivermos três shards,
teremos seis megabytes de agregado para boots
para downstream.
Mas cada fragmento terá dois megabytes para si próprio.
Portanto, agora temos um
aplicativo de consumidor e ele deseja ler, por exemplo, o fragmento número um.
O que será feito é que eles farão uma chamada à API Get Records
e o fragmento retornará alguns dados.
E se o consumidor quiser mais dados, ele precisará
fazer outra chamada à API para obter registros.
Por isso, ele é chamado de mecanismo de sondagem.
Portanto, o Get Records, toda vez que
for executado, retornará até 10 megabytes de dados.
E como os 10 megabytes de
dados ultrapassam o total de dois megabytes por segundo,
será necessário aguardar
cinco segundos até que você faça outro
Get records, ou ele retornará um máximo de até 10.000 registros.
Isso significa, o que é isso?
Há também outro limite que você precisa conhecer.
Primeiro, há um máximo de cinco chamadas
à API Get Records por shards, por segundo.
Isso significa que o aplicativo do consumidor
não pode fazer apenas Get Records, Get records,
20 vezes por segundo.
Ele pode fazer isso apenas cinco vezes por segundo.
Isso significa que você terá uma latência de 200 milissegundos em
seus dados.
Portanto, lembre-se desse número, pois ele é muito importante.
Mas o que isso significa agora?
Se analisarmos essas restrições e começarmos
a adicionar mais consumidores.
Bem, se cinco aplicativos de consumidores
são consumidos do mesmo fragmento, são aplicativos
diferentes e todos eles precisam ler os mesmos
dados, então cada consumidor basicamente pode fazer uma sondagem por
segundo e pode receber menos de 400 kilobytes por segundo.
Isso significa que, quanto mais consumidores você tiver,
menor será a taxa de transferência por consumidor.
Portanto, se adicionarmos o consumidor B e o consumidor C, todos
eles compartilharão esse limite de dois
megabytes por segundo, por fragmento.
E todos eles compartilharão esse limite
de cinco chamadas à API Get Records por segundo.
Portanto, é muito importante entender isso.
E veremos como o Kinesis Enhanced fan-out para os consumidores resolverá
esse problema.
Portanto, a próxima coisa que vamos explorar
é a biblioteca Kinesis Client.
E ela é uma biblioteca que se inicia em Java, mas
também existe para outras linguagens, como
Golang, Python, Ruby, Node e . NET.
A ideia é que, usando o KCL, você possa ler registros
do Kinesis produzidos com o KPL, pois
ele tem um mecanismo de agregação dentro da biblioteca.
Ele também oferece a possibilidade de vários consumidores
compartilharem vários fragmentos usando o conceito de grupo.
E isso significa que há um processo de descoberta de
fragmentos incluído na KCL.
Além disso, há um recurso de apontamento de
verificação para o caso de os aplicativos
ou as fontes de registro ficarem inoperantes,
e eles podem ser retomados de onde estavam
no último processamento.
Ele também aproveita o Dynamo DB para a coordenação
e o apontamento de verificações.
Isso significa que haverá
um novo dynamo DB, uma linha por fragmento.
Isso significa que, como o Dynamo DB está
envolvido no processo de leitura de um fluxo de dados do Kinesis, você
precisa cuidar do provisionamento
da tabela do Dynamo DB.
Isso significa que você precisa ter uma
unidade de capacidade de gravação suficiente, ou
seja, WCU, e uma unidade de capacidade de leitura, ou seja, RCU.
Ou, se não quiser se preocupar com isso,
você pode usar o modo sob demanda para o Dynamo DB e não receber
nenhuma exceção de limitação.
Porque, caso você tenha exceções na tabela do Dynamo DB, o
Dynamo DB será acelerado
e isso poderá tornar mais lenta a leitura
do Kinesis Client Library.
Agora, os processadores de registros processarão os dados.
E se você receber, como eu disse,
uma exceção de iterador expirado, isso significa
que algo está acontecendo em sua biblioteca KCL.
Isso significa que você precisa
aumentar a WCU porque a tabela do Dynamo DB não é rápida o
suficiente para acompanhar as gravações.
Portanto, esta é uma pergunta de exame.
Então, vamos dar uma olhada em como isso funciona.
Portanto, temos um fluxo de dados
do Kinesis, que tem talvez quatro fragmentos,
e temos uma tabela do Dynamo DB que será usada
para apontar a verificação e coordenar nossos
processadores de registros KCL.
Portanto, neste exemplo, tenho dois aplicativos KCL
do mesmo grupo em execução
em duas instâncias diferentes do EC2.
Assim, graças a esse mecanismo de descoberta de fragmentos, eles podem compartilhar
os gráficos.
Portanto, o primeiro estará lendo do fragmento
um e dois e o segundo estará
lendo do fragmento três e quatro.
Em seguida, os aplicativos KCL verificarão
o progresso na tabela do Dynamo DB.
E isso acontece com frequência, o que
significa que você precisa
fornecer WCU suficiente para a tabela do Dynamo DB.
E, novamente, caso você receba uma exceção de iterador expirado,
será necessário aumentar a WCU.
Suas unidades de capacidade de gravação na tabela do Dynamo DB.
Há também a biblioteca de conectores totalmente confusa, também conhecida
como KCL, Kinesis Connector Library.
Trata-se de uma biblioteca Java mais antiga, de 2016, que
aproveita a biblioteca KCL por baixo do capô.
E é usado para gravar dados no Amazon S3 ou
Dynamo DB, Redshift ou OpenSearch.
E a biblioteca do conector deve estar
em execução em uma instância do EC2, por exemplo, para que isso
aconteça.
Portanto, trata-se de um aplicativo cuja única
finalidade é obter dados dos fluxos de dados do Kinesis
e enviá-los a todos esses destinos.
Agora você pode pensar:
"Ah, isso já é algo que podemos fazer
com a mangueira Kinesis Fire. E isso é verdade.
Já podemos fazer isso com a mangueira Kinesis
Fire e veremos isso.
Portanto, para alguns
desses alvos, podemos usar
o Kinesis Fire hose, por exemplo, para S3 e Redshift,
mas para outros podemos usar o AWS Lambda.
Portanto, de modo geral, eu diria que a biblioteca
de conectores do Kinesis pode
aparecer no exame, mas ela está meio obsoleta e foi
substituída pelo Kinesis Fire hose e pelo Lambda.
Então, vamos falar sobre o Lambda agora.
O Lambda pode ler registros de um fluxo de dados do Kinesis.
E o consumidor Lambda também tem uma pequena biblioteca,
que é muito boa, usada
para agregar registros da KPL.
Assim, você pode produzir com
um KPL e ler de um consumidor Lambda usando uma pequena biblioteca.
Agora o Lambda pode ser usado para fazer ETL leve.
Portanto, podemos enviar dados para o Amazon S3, Dynamo DB, Redshift,
OepnSearch ou, na verdade, para qualquer lugar que você queira,
desde que você possa programá-lo.
E o Lambda também pode ser usado para ler em tempo real
os fluxos de dados do Kinesis e acionar notificações ou,
por exemplo, enviar e-mails em tempo
real ou o que você quiser.
Por fim, Frank descreverá isso detalhadamente,
mas há um tamanho de lote configurável e veremos
isso na seção Lambda, mas basicamente você
pode dizer quantos dados por vez o Lambda
deve ler do Kinesis, o que ajuda a regular as colocações.
De modo geral, vimos todas as maneiras de ler
os fluxos de dados do Kinesis.
Há muitos tipos diferentes.
Mas espero que isso coloque algum
contexto sobre qual deles é bom para cada caso de uso.
E eu o verei na próxima palestra.
