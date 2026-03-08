Então,
precisamos saber como podemos produzir dados no Kinesis.
Portanto, aqui estão os fluxos do Amazon
Kinesis e o exame espera que você saiba
em alto nível como cada um deles funciona.
O primeiro é o SDK.
O SDK permite que você escreva códigos ou use a CLI para
enviar dados diretamente para o Amazon Kinesis Streams.
A segunda é usar a Kinesis Producer Library ou KPL,
lembre-se desse acrônimo.
A biblioteca do Kinesis Producer será um
pouco mais avançada.
Você escreverá um código melhor
e ele tem alguns recursos muito
bons que descreverei nesta palestra,
que permitem que você obtenha um rendimento aprimorado
no Kinesis Streams.
A terceira é usar um Kinesis Agent.
Portanto, o Kinesis Agent é um programa Linux que
é executado em seu servidor.
Portanto, lembre-se de que ele é um agente que é executado
em servidores e basicamente permite que você obtenha um arquivo
de registro, por exemplo, e o envie de forma confiável para o Amazon Kinesis Streams.
que geralmente se baseiam no SDK, como Apache Spark, Kafka Connect,
NiFi, etc., e tudo isso permitirá que você envie
dados para o Kinesis Streams de forma confiável.
Portanto, observe este diagrama e lembre-se de que o Kinesis
Streams pode oferecer diferentes maneiras de obter dados
de várias fontes.
Agora vamos nos aprofundar em todos os métodos
do lado esquerdo.
Portanto, o primeiro é usar o SDK do
Producer, que usa a API PutRecord ou PutRecords com um s.
Portanto, sempre que você vir PutRecord, isso significa SDK.
Portanto, com um PutRecord, como o nome
indica, você enviou um registro e, se usar PutRecords
com um s, enviará muitos registros.
O PutRecords usará lotes e, portanto, aumentará
sua taxa de transferência.
Isso ocorre porque você envia muitos
registros como parte de uma solicitação HTTP e, portanto, está economizando
em solicitações HTTP e obtendo maiores taxas de transferência.
No entanto, se você ultrapassar a taxa de transferência,
receberá uma exceção de taxa de transferência provisionada excedida, e é importante
saber como lidar com isso.
Veremos isso no próximo slide.
Agora, esse SDK do Producer pode ser usado de várias
maneiras diferentes.
Você pode usá-lo em seus aplicativos, mas também
em seus dispositivos móveis, como Android, iOS, etc.
Então, quando você optará por usar o SDK do Producer?
Bem, sempre que temos um caso de uso de baixa taxa de transferência ou
não nos importamos com uma latência mais alta, queremos uma API muito simples ou talvez
estejamos trabalhando diretamente com o AWS Lambda.
Esse é o tipo de lugar em
que você usaria o SDK do Producer.
Você também precisa
saber que existem algumas fontes gerenciadas
do AWS para o Kinesis Data Streams.
Portanto, nos bastidores, eles usam o SDK do Producer,
mas você não o vê, e essas fontes gerenciadas serão logs
do CloudWatch para que você possa enviar seus
logs diretamente do CloudWatch para o Kinesis.
Você tem o AWS IoT e veremos isso nesta seção.
E, por fim, o Kinesis Data Analytics é capaz de produzir
novamente no Kinesis Data Streams.
Portanto, lembre-se disso.
Agora, como lidamos com as exceções da API do Kinesis?
Bem, se você receber uma exceção de taxa de transferência provisionada, isso acontecerá
quando você estiver enviando mais dados do que pode.
Por exemplo, você está excedendo o número de megabytes
por segundo ou o número de registros por segundo que
pode enviar a qualquer fragmento.
Portanto, você precisa se certificar de que, ao obter isso,
não tenha um fragmento quente.
Por exemplo, se você tiver o ID do dispositivo como chave e 90% dos
seus dispositivos forem iPhones, você terá uma tecla de atalho,
uma partição de atalho, porque todos os seus
dispositivos são iPhones e todos
irão para a mesma partição.
Portanto, certifique-se de distribuir o máximo possível a chave
que você escolher para não obter uma partição quente.
Portanto, a solução é: se você receber uma exceção de provisionamento de taxa de transferência,
tente fazer novas tentativas com backoff.
Isso significa que você tentará novamente depois de talvez dois segundos e, se não
funcionar, tentará quatro segundos
e depois de oito segundos,
que são apenas números arbitrários.
Ou você pode aumentar o número de fragmentos
que tem no Kinesis basicamente para aumentar a quantidade
de escalonamento que pode fazer.
E você precisa garantir que sua chave de partição
seja boa, uma chave bem distribuída.
Assim, por exemplo, para o dispositivo móvel, em vez de escolher
Apple versus Android, você escolheria talvez
a ID do dispositivo que, com certeza, será diferente para
cada um dos seus usuários.
Apenas um exemplo.
Vamos falar agora sobre a Kinesis Producer Library ou KPL.
Você precisa aprender exatamente como isso funciona,
pois isso é muito importante para o exame.
É uma biblioteca C++ ou Java fácil de usar e altamente configurável
e, em minha experiência pessoal, vi que o
Java é mais usado quando você usa a KPL.
Ele é usado quando você deseja criar produtores
de alto desempenho e longa duração.
E ela tem automação para o mecanismo de repetição, de modo
que a exceção que eu deveria descrever antes,
com a qual temos que lidar ao usar a API,
bem, a Kinesis Producer Library
sabe automaticamente como lidar com isso.
A biblioteca do produtor do Not Kinesis tem dois tipos de APIs.
Há a API síncrona, que é a mesma do SDK, ou a API
assíncrona, que proporcionará melhor desempenho
quando você precisar lidar com assincronia,
obviamente.
Portanto, toda vez que, no exame, você vir
que precisamos enviar dados de forma assíncrona para o Kinesis Data Streams,
geralmente a Kinesis Producer Library ou KPL será a maneira
de fazer isso.
É uma alavanca muito boa porque também é capaz de
enviar métricas para o CloudWatch para monitoramento.
Portanto, sempre que você escrever um aplicativo com um
KPL, poderá monitorá-lo diretamente no CloudWatch.
E ele suporta um mecanismo muito importante chamado batching.
E o batching tem duas subseções, e ambas estão ativadas
por padrão e o ajudarão a aumentar
o rendimento e a reduzir o custo.
Você precisa conhecê-los, com certeza.
A primeira é coletar registros e gravar em vários
fragmentos na mesma chamada à API PutRecords.
E a segunda é a agregação, que aumentou a latência,
mas também aumentou a eficiência.
Portanto, é um recurso que permite armazenar vários registros
em um único registro e, com isso, é possível ultrapassar
o limite de 1.000 registros por registro.
De qualquer forma, vou descrevê-los para você no próximo slide.
E isso permitirá que você aumente o tamanho da carga útil e, portanto,
aumente a taxa de transferência.
Assim, você pode atingir o limite de um megabyte por
segundo de forma mais consistente.
Se você quiser usar a compactação,
ou seja, diminuir o tamanho dos registros,
infelizmente isso não é compatível com a Kinesis
Producer Library.
Você teria que implementar isso por conta própria.
No entanto, quando enviamos um registro com uma biblioteca do Kinesis
Producer, esse é um registro muito especial e não
é possível lê-lo simplesmente usando a CLI.
Para isso, você precisaria usar o KCL ou uma biblioteca
auxiliar especial.
E veremos o KCL na próxima palestra.
Então, vamos falar
sobre esse agrupamento, porque esse é um conceito muito
importante a ser entendido na Kinesis Producer Library e
algo que o exame perguntará a você?
Por exemplo, estou enviando um registro para o Kinesis, com dois
kilobytes, e estou enviando-o
usando a Kinesis Producer Library.
Acontece que ele não será enviado imediatamente.
Ele vai esperar um pouco para ver se mais
registros estão chegando.
E talvez eu esteja enviando um próximo registro de 40 kilobytes.
Talvez eu esteja enviando um próximo registro de 500 kilobytes.
E o que o Kinesis Producer Library fará é que,
em algum momento, ele dirá: "Espere um minuto,
posso agregar todos esses registros em um único registro".
Portanto, em vez de enviar três registros, agora
estamos enviando um registro e esse registro
ainda tem menos de um megabyte.
Vamos fazer isso várias vezes, portanto,
talvez tenhamos um, 30, 80 e 200 kilobytes novamente,
e isso também será agregado
em um único registro.
Portanto, agora temos dois registros.
Então, já vimos o que é agregação.
E então ele dirá, espere um minuto.
Agora temos que enviar dois registros grandes,
mas não vamos usar duas APIs PutRecord, que é uma
delas, e faremos a coleta.
Portanto, usaremos uma API PutRecords.
Então, aqui você vê que eu queria enviar sete registros
para o Kinesis e acabei fazendo apenas uma chamada de API
porque temos agregação e coleta.
E então, como o Kinesis sabe quanto tempo esperar para agrupar
esses registros?
Portanto, poderíamos controlá-lo usando o RecordMaxBufferedTime,
cujo padrão é 100 milissegundos.
Basicamente, você está dizendo:
"Tudo bem, estou disposto a esperar
100 milissegundos", o que adiciona um pouco de latência
e a compensação de ser mais eficiente.
Portanto, se você quiser menos atraso, diminua essa
configuração e, se quiser mais
lotes, aumente essa configuração.
Então é isso para a KPL.
Lembre-se de que o mecanismo de lote é muito importante.
Portanto, há uma situação em que talvez você não queira
usar uma Kinesis Producer Library,
e isso é algo que pode surgir no exame.
Portanto, quando você usa o KPL, pode incorrer em um atraso
de processamento adicional de até RecordMaxBufferedTime, portanto,
essa é uma configuração configurável pelo usuário na biblioteca.
A ideia é que quanto mais tempo você tiver esse buffer, portanto,
quanto maior for o valor do RecordMaxBufferedTime, maior será
a eficiência do empacotamento e melhor será o
desempenho, pois mais registros
serão acumulados nesse buffer e serão enviados como um registro maior,
o que será mais eficiente, potencialmente compactado
e assim por diante.
Mas se você tiver um aplicativo que não tolera um atraso
adicional, talvez seja necessário usar o AWS
SDK diretamente.
Isso significa que você deseja enviar os dados imediatamente.
Então, vamos dar um exemplo.
Se você tiver um sensor de IoT e ele vier com um SDK do AWS, e quiser
produzir para o Kinesis Data Streams.
Mas esse sensor de IoT às vezes fica off-line.
Portanto, se você usar o KPL e houver um evento off-line,
o que acontecerá é que o KPL manterá
os dados e os acumulará.
Isso significa que, quando meu dispositivo voltar
a ficar on-line, pode demorar um pouco para que os dados mais
recentes cheguem ao meu fluxo de dados do Kinesis, e talvez
queiramos apenas pedir para agir com base nos dados mais recentes.
Portanto, nesse caso, em vez de usar o KPL, será
mais sensato implementarmos nossos aplicativos que
estejam claramente usando o nome de chamadas da API do SDK PutsRecords porque,
quando usamos PutRecords, podemos optar por descartar
todos os dados e enviar somente os dados mais recentes e relevantes
quando meu dispositivo estiver on-line.
Portanto, agora você conhece esse caso
de uso, e ele pode aparecer no exame.
A última maneira de produzir para o Kinesis é usar o Kinesis Agent.
Portanto, esse agente será basicamente instalado
e monitorará os arquivos de registro e os enviará diretamente para o
Kinesis Data Streams.
É apenas uma configuração a ser feita.
É um agente baseado em Java e, na verdade, foi desenvolvido
com base na biblioteca KPL.
Isso o torna realmente confiável e eficiente.
Por enquanto, você instalaria
isso apenas em ambientes de servidor baseados em Linux.
Portanto, os recursos são gravar a partir de vários diretórios
e gravar em vários fluxos, com um recurso de roteamento baseado no diretório
ou no arquivo de registro que você está usando e pode até mesmo
pré-processar os dados antes de enviá-los aos fluxos de
dados do Kinesis.
Ele pode fazer divisões de linha única, pode transformar csv em
json, registrar em Jason e, além disso, a versão do Kinesis é muito
bem escrita.
Portanto, ele tratará de tudo, como rotação de arquivos de registro,
pontos de verificação e novas tentativas em caso de falhas.
E como ele usa a biblioteca KPL, emitirá
métricas baixas para o CloudWatch para monitoramento.
Portanto, sempre que precisar fazer a agregação de logs em
massa quase em tempo real, o Kinesis Agent é
o caminho a seguir.
Tudo bem.
Portanto, vimos todas as maneiras de produzir no Kinesis.
Sei que é muita coisa, mas lembre-se de que, em um nível alto,
você precisa entender como eles
funcionam e espero ter conseguido isso.
Eu o verei na próxima palestra.
