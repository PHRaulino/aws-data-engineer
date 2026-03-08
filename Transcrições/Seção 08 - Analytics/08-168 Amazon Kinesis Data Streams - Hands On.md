o Kinesis Data Streams.
Então, vou abrir o serviço do Kinesis e criar nosso primeiro
Kinesis Data Streams.
Como podemos ver, temos três opções aqui.
Podemos usar Data Streams, Data Firehose ou Data Analytics, mas
até o momento só conhecemos Data Streams, então
vamos em frente.
Obtemos algumas informações sobre
o preço, que é por fragmento, pagamos US$ 0. 05 por hora.
Está bem.
E há um custo para fazer PUTs ou para enviar
dados para o Kinesis Data Streams.
Então, vamos criar um fluxo de dados, vamos
nomear nosso fluxo como DemoStream e, em seguida,
precisamos definir a capacidade do fluxo de dados.
Portanto, como você pode
ver, temos dois modos: o modo On-demand e o modo Provision.
E no modo On-demand, você não
precisa se preocupar com a capacidade, ela é dimensionada
automaticamente para você, portanto,
há uma taxa de transferência máxima de 200 megabytes por segundo e 200.000
registros por segundo, e a capacidade
máxima de leitura de 400 megabytes por segundo, por consumidor, se você estiver
usando a opção Fan-Out aprimorada.
Portanto, o modelo de preços sob demanda é pago por taxa de transferência, mas
não há uma camada gratuita. Está bem.
E o modo Provisão também não tem um nível gratuito.
E no modo de provisionamento, você precisa provisionar shards.
Portanto, há uma ferramenta de estimativa de fragmentos,
caso você queira saber quantos fragmentos são necessários,
com base em quantos registros você envia por segundo, qual é o tamanho do seu registro
e quantos consumidores você tem.
Mas, em um exemplo, vamos configurar apenas um fragmento.
Está bem.
Um fragmento nos dá um megabyte por segundo para gravação
e dois megabytes por segundo para leitura.
E, obviamente, se você colocar 10 fragmentos,
tudo será multiplicado por 10. Certo, então um fragmento
é suficiente para fazermos a demonstração.
É também a opção mais barata que podemos obter.
Se você não quiser pagar nada neste curso, não faça este
curso prático, porque você
pagará algum dinheiro pelo seu fragmento,
embora nós lide com ele e o exclua
com rapidez suficiente.
Portanto, quando estiver pronto, basta clicar em Create data stream (Criar
fluxo de dados) e aguardar a criação do fluxo de dados.
E agora nosso fluxo foi criado com sucesso.
Portanto, em termos de aplicativos, podemos
ver que temos produtores e três opções recomendadas.
Os agentes do Kinesis, o SDK ou a biblioteca do produtor
do Kinesis.
Portanto, todos eles estão disponíveis no GitHub, para que você possa dar uma olhada.
Essa é uma maneira de transmitir dados de servidores de aplicativos
para o Kinesis Data Streams.
O SDK serve para que você desenvolva produtores em um nível muito baixo.
E a KPL serve para que você desenvolva produtores
em um nível muito alto, com uma API melhor.
E, em termos de consumidores,
temos o Kinesis Data Analytics, o Kinesis Data Firehose ou o
Kinesis Client Library, ou o Lambda, que também não é mostrado
como uma opção aqui.
Está bem. Obtemos algumas informações de monitoramento
sobre nossos fluxos de dados do Kinesis.
Então, quantos registros estamos enviando para ele?
Podemos dar uma olhada na configuração.
Portanto, se você quiser dimensionar o fluxo,
podemos dizer quantos fragmentos queremos.
Podemos ir de um para, digamos, cinco, e
dimensionar nosso fluxo de dados do Kinesis.
Poderíamos adicionar algumas
tags e, em seguida, usar o Fan-Out aprimorado e configurá-lo,
se quiséssemos ter alguns aplicativos de consumidor
aproveitando o recurso Fan-Out aprimorado.
Mas, por enquanto, vamos manter a simplicidade.
Queremos apenas escrever e ler em nosso fluxo
e, portanto,
usaremos o SDK para produzir e consumir.
Para isso, queremos abrir uma CLI, e vamos usar
o CloudShell porque é divertido.
Então, vou clicar no CloudShell bem aqui,
que é o ícone, ao lado do ícone do sino.
E isso vai abrir, para mim.
uma interface de linha de comando no AWS.
Como alternativa, você poderia usar seu próprio terminal
ou CLI, se estiver pré-configurado,
mas eu gosto de mudar as coisas, e este aqui me agrada
muito porque, pelo menos,
há menos configuração envolvida.
Criar o ambiente, pela primeira
vez, pode levar algum tempo, e o CloudShell é gratuito no AWS, portanto,
não se preocupe.
Enquanto isso, no Kinesis, abra o kinesis-data-streams.
e vamos usá-lo de modo geral.
sh,
Portanto, há dois tipos
de comandos para gravar no Kinesis Data Stream com base em sua
versão da CLI do AWS.
Portanto, normalmente, você tem a versão dois instalada,
mas é possível que, de alguma forma, tenha
a versão um instalada.
Para obter a versão,
basta digitar aws --version e colar, e então você obterá
algumas informações sobre
a versão da CLI do AWS.
Portanto, no CloudShell, a
versão da CLI que será instalada é a versão dois, como você pode ver
aqui, era a versão 2 da CLI. 1. 16, portanto, usaremos
a versão dois dos comandos da CLI.
Mas se você quisesse ter a versão um, então
usaria esses comentários.
Está bem. Então, agora estamos prontos para ir.
A primeira coisa que queremos fazer é enviar um registro
para o nosso Kinesis Data Stream.
E, para isso, há uma API chamada put-record.
E no put-record, precisamos especificar um nome de fluxo.
Portanto, neste exemplo, não dei o nome de teste ao meu fluxo,
mas sim de DemoStream, portanto,
teremos que alterar isso no comando da CLI, mas você entendeu
a ideia.
Em seguida, você especifica uma chave de partição para as configurações de dados.
Portanto, o usuário um, e lembre-se de que os dados que compartilham
a mesma chave de partição irão para
o mesmo fragmento, mas temos apenas um fragmento, portanto,
isso não importa neste caso.
Depois, os dados em si, para que os usuários se inscrevam.
E, finalmente, como estamos gravando alguns dados
de texto, precisamos dizer essa opção cli-binary-format
raw-in-base64-out.
Está bem. Então, deixe-o colar esse comando,
copie e cole, mas deixe-me apenas editar o nome do fluxo,
para ter certeza de que é DemoStream.
E o canal na nuvem é configurado automaticamente
com suas próprias credenciais de IM,
portanto, ele herdará o que você tiver como credenciais de IM
e, além disso, usaremos a região por padrão, na qual ele foi
iniciado.
Portanto, us-east-1.
Pressiono Enter.
E agora, recebemos uma mensagem de sucesso.
Portanto, a mensagem foi enviada shardId-0000000000000.
Portanto, nosso primeiro fragmento e o número de sequência
da mensagem estão aqui.
Se eu fizer isso novamente, receberei uma segunda mensagem com um sucesso, para que
possamos fazer a inscrição do usuário.
Podemos misturar a mensagem,
depois o login do usuário e, em seguida, talvez o logout do usuário.
Portanto, estamos apenas configurando algumas
mensagens em nosso Kinesis Data Stream.
Perfeito. Então, vou limpar
isso e, se você esperar um pouco,
entrar no monitoramento e olhar as métricas de fluxo, vou colocá-las em uma hora,
você verá um registro de colocação
bem aqui, mas leva um pouco de tempo para que as métricas
do CloudWatch sejam atualizadas,
mas você as verá aqui. Está bem.
Em seguida, queremos poder consumir o fluxo de
dados do Kinesis.
Portanto, para fazer isso, primeiro descreveremos o fluxo para obter algumas
informações sobre a composição desse fluxo, pois precisamos
ser capazes de consumir de um fragmento específico.
Então é DemoStream, vou pressionar Enter e, como você pode ver
aqui, temos esse StreamDescription.
Temos um fragmento chamado shardId-0000000000000 e, portanto,
precisamos ter isso em mente. Está bem.
Para poder ler a partir desse fluxo.
Portanto, quando você usa a CLI, o SDK
em um nível muito, muito baixo, precisa especificar
de qual fragmento está lendo.
Mas se você estiver usando a Biblioteca de Clientes Kinesis,
tudo isso será tratado pela própria biblioteca.
Mas como estamos usando a CLI,
precisamos especificar o ID do fragmento.
Então, pressiono Q para sair disso e vou consumir
alguns dados.
Então, vou executar este comando, bem aqui,
e deixarei isso claro.
E há duas coisas a observar: a primeira
é que preciso alterar o nome do fluxo do qual estou consumindo.
Portanto, o DemoStream é um fluxo e o tipo
de shard-iterator é TRIM-HORIZON.
Isso significa que você lerá desde o início
do fluxo, portanto,
lerá todos os registros que foram
enviados desde o início.
A outra opção é certificar-se de receber apenas os registros
a partir desse momento, quando um novo comando
CLI for iniciado.
De qualquer forma, vou pressionar Enter.
E isso vai me dar um ShardIterator.
E esse ShardIterator pode ser reutilizado para consumir registros,
portanto, o próximo comentário
da API é kinesis get-records --shard-iterator.
Em seguida, especificamos toda essa cadeia de caracteres, bem aqui.
Portanto, esse modo de consumo que estou fazendo
agora, usando a API de baixo nível, descrevendo
o fluxo, obtendo um ShardIterator e obtendo registros,
está usando o modo de consumo compartilhado.
Isso não está usando o Fan-Out aprimorado,
que, na minha opinião, deveria
estar usando a Biblioteca do cliente Kinesis, a Biblioteca do consumidor
para que você realmente aproveite e tenha uma boa API para fazer
isso.
Mas isso é de baixo nível.
Então, vamos clicar e pressionar Enter
no Kinesis get-records,
e obteremos um lote de registros.
Portanto, costumávamos ter o registro um
aqui, que é PartitionKey user1.
E temos alguns dados aqui, mas eles estão codificados em base64.
Temos, novamente, outro dado, codificado em base64.
Obtemos algumas informações de registro de data e
hora, outros dados codificados em base64.
E, se eu pressionar Enter, ele
vai diminuir um pouco.
Mais alguns dados codificados em base64.
Então, para ter certeza de
que podemos ler os dados, posso acessar os sites, base
64 decode online, e vou colar esses dados aqui,
na base 64 decode, e clicar em DECODE, e
isso nos dá o registro do usuário.
E se eu colar o segundo tipo de dados,
este, copiar e colar aqui, nos dará o login do usuário.
Então, foi isso que enviamos.
Portanto, isso é perfeito.
Tudo está funcionando.
E então, como você pode
ver, há um argumento NextShardIterator bem aqui.
Portanto, na próxima vez que consumirmos,
precisaremos especificar esse argumento NextShardIterator para consumir
a partir de onde paramos de consumir.
Portanto, isso é algo que você precisa iterar em seu código.
Mas, em um nível baixo, produzimos
dados para o Kinesis Data Stream e consumimos
dados do Kinesis Data Stream, o que é incrível.
E, nesse meio tempo, também usamos o CloudShell,
que considero muito útil.
Então é isso para esta
demonstração, mantenha esse fluxo aberto, pois o usaremos
para o Kinesis Data Firehose em um segundo.
E eu o verei na próxima palestra.
