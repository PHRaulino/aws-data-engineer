o Kinesis Data Streams e agora o Firehose.
Portanto, o Firehose é realmente muito fácil.
Ele serve para armazenar dados em destinos de destino.
Portanto, temos produtores e pode ser,
novamente, um monte
de aplicativos anteriores que
podem enviar diretamente os dados
para o Kinesis Data Firehose ou o Kinesis
Data Firehose pode ler do
seu Kinesis Data Stream, do Amazon CloudWatch ou do AWS IoT.
Mas o mais comum que você
verá será a leitura do Firehose do Kinesis Data Streams.
Portanto, ele lerá os registros, um por um,
até um megabyte por vez.
Está bem?
E, se quisermos transformar o registro,
podemos ter uma função Lambda criada para transformar
o registro e fazer alguma pequena modificação.
E então, o Kinesis Data Firehose tentará preencher um grande lote de dados
para gravar esses dados em um banco de dados de destino
ou em um destino de destino, certo?
Por isso, é chamado de gravação em lote.
Ele não escreve coisas instantaneamente.
Ele tentará agrupá-los para escrevê-los com eficiência.
Portanto, o Kinesis Data Firehose
é um serviço quase em tempo real.
Portanto, em termos de destinos, temos a AWS.
Portanto, o Amazon S3 é muito importante, o Amazon Redshift e, para
gravar no Redshift,
o Kinesis Data Hose primeiro grava no Amazon S3 e depois
emite um comando de cópia no Redshift ou
no Amazon OpenSearch.
E você precisa se lembrar desses três destinos,
pois eles são muito importantes.
Outros destinos incluem destinos de terceiros de
parceiros como Datadog, Splunk,
New Relic e MongoDB, mas é possível que
outros venham a surgir no futuro.
Você não precisa conhecê-los,
por isso não atualizaremos este slide se houver novos
parceiros, mas você pode
ver que haverá novos parceiros ao longo do tempo ou,
também, pode haver um destino personalizado.
Desde que haja um ponto de extremidade HTTP válido como uma API,
você pode fazer com que o Firehose
forneça dados para esse destino.
E, por fim, se houver falha no processamento
ou se você quiser arquivar todos os dados que vão
para o Firehose, é muito possível enviar
todos os dados ou apenas um dado com falha para um bucket S3
de backup do Kinesis Data Firehose.
Bem, o Kinesis Data Firehose é um serviço totalmente gerenciado.
Não requer administração e é considerado
quase em tempo real porque você tem
um buffer baseado no tempo gasto no buffer e no tamanho
do buffer e, em seguida, os dados são
entregues ao seu destino.
Agora existe a opção de desativar esse buffer.
Então, para que você usa o Firehose?
Bem, você carregará dados no Redshift, Amazon
S3, OpenSearch ou Splunk.
Você precisa se lembrar de cor desses quatro destinos.
Portanto, lembre-se do Redshift, do S3, do OpenSearch e do Splunk.
O que é realmente interessante no Kinesis Data
Firehose é que, diferentemente do Kinesis Data
Streams, há um dimensionamento automático.
Isso significa que, se você precisar de mais
taxa de transferência, o Kinesis Data Firehose será dimensionado para você.
E se você precisar de menos, ele também será dimensionado para você.
Ele também é compatível com vários formatos
de dados e pode fazer a conversão de dados.
Por exemplo, de JSON para Parquet/ORC se você usar o S3.
As outras transformações de dados que você pode
fazer são realizadas por meio do AWS Lambda.
Por exemplo, se você quisesse
transformar um arquivo CSV em um arquivo JSON, poderíamos
usar o AWS Lambda para fazer essa transformação
em conjunto com o Kinesis Data Firehose.
Também oferece suporte à compactação quando o destino é o Amazon S3.
Assim, podemos compactar os dados que estão
sendo enviados em GZIP, ZIP ou SNAPPY diretamente no S3.
E se você carregá-lo no Redshift mais adiante,
o GZIP será o único
mecanismo de conversão compatível.
Por fim, você pagará apenas pela
quantidade de dados que passa pelo Firehose.
E o mais legal é que, se você não precisar
provisionar o Firehose com antecedência, não será
cobrado pela capacidade de provisionamento,
mas apenas pela capacidade utilizada.
Por fim, um exame fará com que você pense que o Spark ou
o KCL pode ler o KDF ou o Kinesis Data Firehose.
Esse não é o caso.
O Spark Streaming e o Kinesis Client Library
não leem do Firehose.
Eles só leem dos fluxos de dados do Kinesis.
Então, eu só queria deixar isso muito, muito claro agora.
Então, qual é a aparência do diagrama de entrega?
Bem, temos o Firehose no meio, e ele
terá uma fonte, por exemplo, minha
fonte neste exemplo é o Kinesis Data Streams.
Portanto, ele enviará esse fluxo para
o Firehose e talvez possamos fazer alguma transformação de dados.
Portanto, lembre-se de que eu disse CSV para JSON.
Na verdade, há vários projetos disponíveis para o AWS
Lambda para tentar ajudá-lo a transformar os dados no Firehose
no formato desejado.
Depois que os dados são formatados e transformados,
podemos enviar os resultados, por exemplo, para
um bucket do Amazon S3.
Se o S3 for seu destino, ou se o Redshift
for seu destino, na verdade, ele passará pelo
S3 e, em seguida, será emitido um comando
de cópia para colocar esses dados no Redshift.
E quanto aos registros de origem?
Podemos colocar os registros de origem em um bucket S3?
A resposta é sim.
Qualquer registro de origem que
passe pelo Kinesis Data Firehose pode ser
configurado para aterrissar em outro bucket de sua escolha.
Portanto, se o exame perguntar a você:
"Ok, como colocamos todos esses dados de origem em um bucket do Amazon S3 por meio
do Kinesis Data Firehose?
Bem, esse é diretamente um recurso do Firehose.
Há também um recurso muito bom.
Caso haja uma falha de transformação,
podemos arquivar a falha de transformação
em um bucket do Amazon S3, ou mesmo
se houver uma falha de entrega, bem, também podemos ter
essa falha de entrega colocada
em um bucket do Amazon S3.
O que você se lembra disso, desse diagrama,
é que você não perde dados com o Kinesis Data Firehose.
Ou ele termina em seus alvos ou
você terá uma lembrança de todas as falhas de transformação,
de entrega e até mesmo dos registros de
origem, caso queira
colocá-los em outro bucket do S3.
Portanto, lembre-se de que, nesse diagrama, é muito importante...
Esse é basicamente o seu
entendimento do Kinesis Data Firehose.
Agora, vamos analisar a frequência
com que o Kinesis Data Firehose envia os
dados de saída para os destinos.
E, para isso, precisamos entender
o dimensionamento do buffer do Firehose.
Então, como funciona o Firehose?
Bem, o Firehose receberá um monte de
registros da fonte e acumulará todos
esses registros em um buffer.
E esse buffer, daí seu nome, não é
liberado o tempo todo.
A descarga é feita com base em algumas regras.
Ele se baseia em regras de tempo e tamanho.
Portanto, precisamos definir um tamanho de buffer,
por exemplo, 32 megabytes.
Isso significa que, se você tiver dados suficientes
da origem que atinjam e preencham um buffer de 32 megabytes, então,
automaticamente, eles serão liberados.
A outra configuração é o tempo de buffer, por exemplo, dois minutos.
Isso significa que, se após
dois minutos o tamanho do buffer não estiver cheio,
ele será liberado.
Portanto, o Firehose, desculpe, pode aumentar automaticamente o tamanho do buffer para
aumentar as taxas de transferência.
Portanto, ele é muito bem dimensionado para você e acomoda
qualquer tamanho de taxa de transferência.
Portanto, se tivermos uma alta taxa de
transferência, ou seja, muitos dados passando pelo Kinesis Firehose, o limite
de tamanho do buffer será atingido e a descarga será feita
com base no tamanho do buffer.
Mas se tivermos baixas taxas de transferência,
normalmente, isso significa que o limite de tamanho do buffer não
será atingido, mas, em vez disso, o limite de tempo do buffer será atingido.
Agora, o tempo de buffer, o mínimo que você pode definir é um minuto.
E o tamanho do buffer, você pode definir alguns megabytes.
Então, Kinesis Data Streams versus Firehose?
Eles parecem semelhantes, mas na verdade não são.
Streams é que você terá que escrever um código personalizado
para seu produtor e seu consumidor, e será em
tempo real, teremos uma latência
de 200 milissegundos para consumidores
clássicos ou 70 milissegundos para consumidores com fan-out
aprimorado.
E você mesmo deve gerenciar o dimensionamento.
Portanto, você precisa realizar a divisão
e a fusão de fragmentos para que seu custo e sua taxa
de transferência se movam ao longo do tempo.
Você tem armazenamento de dados de um a 365 dias, capacidade
de reprodução e vários consumidores.
Você também pode usá-lo no Lambda para
inserir dados em tempo real no OpenSearch, por exemplo.
O Firehose, por outro
lado, será totalmente gerenciado, com dimensionamento
automático, e enviará dados para o S3, Splunk, Redshift
e OpenSearch para você.
Além disso, ele tem algumas transformações de dados sem servidor
que podem ser feitas com o AWS Lambda e quase em tempo real.
É um dimensionamento automatizado e não há armazenamento de dados.
Portanto, o Firehose não reproduz dados ou coisas do gênero.
Portanto, você precisa realmente ver as diferenças entre os dois.
Para mim, eles são claros quanto ao que são, mas você
precisa se lembrar.
Por fim, lembre-se de que, com o produtor do KPL,
você pode produzir em Streams ou Firehose.
Isso é bom.
Portanto, lembre-se de seu caso de uso.
Se o seu caso de uso for fazer com que os aplicativos leiam dados, talvez seja necessário
usar Streams.
Mas se o seu caso de uso for apenas o envio de dados para o S3, Redshift
ou Splunk, talvez o Firehose
seja um caso de uso para você.
E lembre-se das restrições
de tempo real versus tempo quase real.
Então, isso é para o Firehose.
Espero que tenham gostado
e nos veremos na próxima palestra.
