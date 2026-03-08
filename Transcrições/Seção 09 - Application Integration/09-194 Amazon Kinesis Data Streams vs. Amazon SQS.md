Então,
será saber quando usar o Kinesis Streams e o SQS.
Portanto, o Kinesis Data Streams é uma ferramenta de big
data e, quando os dados estão no fluxo, podem
ser consumidos várias vezes por diferentes aplicativos.
Os dados são excluídos somente após o período de retenção, e
esse é o recurso que
permite que os dados sejam consumidos várias vezes.
Em termos de ordenação dos
registros, ela é preservada em um nível de fragmento,
mesmo durante as repetições,
o que é muito útil e permite
distribuir suas leituras no Kinesis Data
Streams.
Também é possível criar
vários aplicativos que leiam
o mesmo fluxo de forma independente,
permitindo, portanto, uma arquitetura do tipo Pub/Sub.
E se você usar, por exemplo,
uma estrutura de Big Data, como Spark ou Flink, poderá
fazer o Streaming MapReduce sobre o
Kinesis Data Streams.
Além disso, se você quiser saber
até onde está lendo sobre os fluxos de dados do Kinesis,
poderá fazer um checkpointing para acompanhar
o progresso, e é isso que a KCL, a biblioteca de clientes do Kinesis,
faz usando o DynamoDB como recurso de checkpointing.
Por fim, o Kinesis Data Streams tem dois modos:
o modo provisionado,
em que você escolhe a capacidade com antecedência,
ou o modo sob demanda, que se adaptará à capacidade ao longo do tempo.
Para o SQS, a situação é muito diferente.
É uma fila, como o nome indica.
Ele é usado para desacoplar aplicativos,
e você só tem um aplicativo de leitura por fila.
E os registros, depois de lidos, são
excluídos após o consumo.
Portanto, se forem reconhecidos, serão excluídos ou, se
falharem várias vezes, poderão
ir, por exemplo, para uma fila de cartas mortas.
As mensagens são processadas de forma independente
para a fila padrão.
Isso significa que você pode processar, por
exemplo, 1.000 mensagens por vez.
No SQS, isso é totalmente possível.
Se você quisesse restrições de
ordenação, precisaria usar filas FIFO,
o que reduz a taxa de transferência, mas
oferece restrições de ordenação.
Você também pode atrasar as mensagens
e o SQS é dimensionado dinamicamente.
Não há operações a serem executadas para dimensionar o SQS.
Portanto, acho que podemos
ver que eles são muito diferentes em termos de casos de uso.
Um é para streaming, streaming de dados e aplicativos.
O outro é mais para desacoplar aplicativos
e criar filas de aplicativos.
Agora, há uma pequena tabela útil que montei para você, que compara
os fluxos de dados do Kinesis, o Kinesis
Data Firehose, o SQS Standard e o SQS FIFO.
Portanto, todos eles são gerenciados pela AWS.
A ordenação está ocorrendo no nível
do fragmento e da chave no Kinesis Data Streams,
ao passo que está ocorrendo
apenas para o ID do grupo específico no SQS FIFO.
E para os outros dois, isso não
está acontecendo.
Para entrega, é pelo menos uma vez nos
três primeiros serviços
e exatamente uma vez para o Amazon SQS FIFO.
Há um recurso de reprodução para o Kinesis Data Streams, enquanto
não há nenhum recurso de reprodução para os outros.
A retenção máxima de dados é de 365 dias para o Kinesis Data Streams e de zero
dias para o Kinesis Data Firehose,
de modo que os dados são simplesmente
enviados para o destino e esquecidos.
E para SQS padrão e SQS
FIFO, são 14 dias.
Em termos de dimensionamento e taxas de transferência,
temos dois shards de provisionamento para o
Kinesis Data Streams no modo provisionado.
Portanto, temos um megabyte por segundo por produtor por fragmento,
ou dois megabytes por segundo por consumidor por fragmento.
E para o modo sob demanda, você tem
o escalonamento que quiser e não precisa escolher
o número de fragmentos
com antecedência.
Não há limites de dimensionamento para
o Kinesis Data Firehose e o SQS Standard.
E para o SQS FIFO, você tem
3.000 mensagens por segundo com batching,
ou 30.000 mensagens por segundo com batching, se você
usar o modo de alto rendimento para o SQS FIFO.
Em termos de tamanho do objeto,
o tamanho máximo do objeto é de um megabyte
para o Kinesis Data Streams.
128 megabytes no destino para o Kinesis Data Firehose, um megabyte
para o SQS, mas você pode estendê-lo
se usar a Extend Library para armazenar as
mensagens fora do SQS e enviar apenas
alguns metadados no SQS.
Portanto, acho que agora sabemos que eles são muito diferentes.
Para os casos de uso do SQS, você tem
filas de processamento de pedidos, processamento de imagens ou escalonamento
automático de acordo com as mensagens ou para armazenar
mensagens em buffer e em lote para processamento futuro ou para descarregar
uma solicitação de um serviço para outro.
Já os fluxos de dados do Kinesis têm diferentes
casos de uso, por exemplo, coleta
e processamento rápidos de dados de registros
e eventos, métricas e relatórios em
tempo real, captura de dados móveis, análise de dados em tempo
real, feed de dados de jogos,
processamento de fluxos complexos, feed
de dados da Internet das Coisas.
Esperamos que agora você entenda as diferenças
entre os dois.
Você está muito confiante nisso e espero
que tenha gostado da palestra.
Eu o verei na próxima palestra.
