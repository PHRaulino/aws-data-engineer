maneira interessante
de usar o Lambda para conectar o S3 ao serviço Opensearch da Amazon.
O Opensearch é basicamente a versão do Elastic Search da Amazon. O motivo
pelo qual ele tem um nome diferente e por que
se ramificou é uma história mais longa.
Falaremos sobre o Opensearch com muito mais
detalhes mais adiante
no curso, mas o que você precisa saber sobre o Opensearch por enquanto
é que ele é, bem, um mecanismo de busca, certo?
Mas ele também pode ser reaproveitado
como um mecanismo de análise.
Portanto, é apenas uma maneira de ingerir um monte de informações,
sejam elas textuais ou numéricas, e pesquisar e consultar
esses dados de maneiras interessantes, além de visualizá-los.
Portanto, um caso de uso comum seria algo como criar
sua própria versão interna do Google Analytics.
Você pode alimentar uma série de dados de registro,
por exemplo, que podem estar sendo despejados em um lago de
dados no S3, e talvez queira visualizar esses dados
de registro para ver quais são as tendências na latência do servidor,
o número de erros relatados ou coisas do gênero.
Portanto, não é possível vincular diretamente um data lake do S3
ao serviço Opensearch da Amazon.
Você precisa de algo intermediário
e, nesse caso, o Lambda seria essa cola.
Portanto, a maneira como isso funcionaria seria despejar os dados dos
seus logs no S3, por meio da mangueira de incêndio do Kinesis ou de qualquer
mecanismo que você desejar.
E quando esses dados são despejados lá, o Lambda
pode ser acionado automaticamente para
processar esses novos dados.
Assim, o S3 pode dizer, ei, Lambda, tenho alguns dados novos para você.
Minha função Lambda pode, então, ingerir esses dados do S3, transformá-los
da maneira que eu precisar, alterar seus tipos de dados, estruturá-los
da maneira esperada pelo Opensearch e, em seguida,
alimentar essas informações quase em tempo real
para o serviço Opensearch da Amazon.
A partir daí, posso usar as ferramentas do Opensearch
para visualizar esses dados, consultá-los e fazer o que quiser.
Portanto, essa é uma aplicação útil do Lambda, que serve
de ligação entre outros serviços, nesse caso,
dados de registro no S3 e a ferramenta de visualização e pesquisa
no serviço Opensearch da Amazon.
Outro exemplo de uso do
Lambda seria com o pipeline de dados.
Portanto, o Data Pipeline, mais uma vez,
é o método da AWS de encadear um processo para processar, importar
e analisar seus dados em um pipeline de dados.
Portanto, a ideia aqui é que, novamente, você
pode querer fazer isso sob demanda à medida que novos dados são recebidos.
Agora, normalmente com o Data
Pipeline, você agenda esses pipelines
para que possa configurar uma pré-condição que
verifique se há novos dados no S3 antes de iniciar,
mas ele ainda será executado
em uma programação regular
normalmente.
Mas, usando o Lambda, você pode iniciar isso sob demanda.
Portanto, se você tiver novos dados sendo recebidos no
S3 e não souber quando eles chegarão,
eles não estarão chegando em uma programação regular.
Usar o Lambda pode fazer sentido.
A maneira como isso funcionaria
seria, novamente, você teria que enviar um acionador S3 para o Lambda
quando novos dados fossem recebidos.
O Lambda, por sua vez, daria a volta
e iniciaria o pipeline de dados assim que esses dados chegassem.
Dessa forma, você pode processar os dados assim que eles forem
recebidos, em vez de fazê-lo de acordo com uma programação regular
que você definiu antecipadamente.
Ele também pode ser usado com o Redshift.
E o Redshift, mais uma vez, é o produto de data warehouse
da Amazon e um grande foco do exame.
Agora, a melhor prática para carregar dados no Redshift
é usar o comando copy.
Você sabe, basicamente um comando
para dizer: copie os dados daqui e coloque-os no Redshift.
Mas, novamente, se você precisar responder a novos
dados que podem aparecer a qualquer momento, talvez seja melhor usar o AWS Lambda
para fazer isso automaticamente quando esses novos dados chegarem.
Portanto, mais uma vez, a ideia seria que o S3 acionasse o Lambda
sempre que novos dados chegassem e, em seguida, ele pudesse
carregar esses novos dados no Redshift.
O problema aqui é que o Lambda é um serviço sem estado.
Ele não consegue manter o controle de onde você parou sozinho.
Então, como o Lambda sabe onde
começar e onde parar quando está
importando dados do S3 para o Redshift?
Bem, para fazer isso,
você precisa usar algo como o DynamoDB
para armazenar onde você parou.
Então, novamente, como o AWS não tem estado por si só, se
você tiver um estado persistente que precise manter,
como, por exemplo, onde parei de importar esses dados, você
terá que se conectar a algo como o DynamoDB
para acompanhar isso.
Portanto, a ideia aqui é que o DynamoDB mantenha o controle dos arquivos que já
foram carregados, quando foram carregados
e em qual tabela, e esses dados seriam usados para
agrupar novos arquivos e copiá-los juntos usando
o comando copy no Redshift.
O Lambda também pode ser usado com
o Kinesis, e já vimos isso antes.
Então, digamos que você tenha dados de streaming do Kinesis em andamento.
Agora, o seu código Lambda receberá um evento
com um lote de registros de fluxo, ok, chegando, e você
pode especificar o tamanho do lote
ao fazer isso, até 10.000 registros.
Agora, isso parece bastante simples, você sabe, os dados
de streaming chegam ao Lambda, você pode
canalizá-los para o Amazon Kinesis e o processamento
posterior acontece.
Mas há muitas pegadinhas que podem acontecer
ao longo do caminho, e um grande foco
do exame é que eles adoram apresentar
esses cenários em que algo dá terrivelmente
errado em seu aplicativo e você precisa descobrir a melhor
maneira de corrigi-lo.
Portanto, esses pequenos detalhes podem ser muito importantes.
Portanto, você precisa saber que, se o tamanho
do lote para dados de streaming for muito grande,
isso poderá fazer com que o serviço Lambda não atinja o tempo limite.
Agora, há um limite superior
para o tempo de execução de uma função Lambda, que,
por padrão, é de 900 segundos no máximo, mas que pode ser
configurado para ser ainda menor.
Portanto, se a sua função Lambda levar muito tempo para processar
esse lote de dados de streaming, ela poderá falhar e isso causará
um tempo limite, o que fará com que todo
o sistema sofra backup.
Portanto, essa pode ser uma fonte de erros.
Agora, os lotes também podem ser divididos além
do limite de carga útil do Lambda.
Portanto, além de um limite de tempo
limite, há também um limite de carga útil de seis megabytes.
Portanto, você teria que tomar medidas
especiais para garantir que seus lotes sejam
divididos se eles excederem seis megabytes
de dados, o que é outra possibilidade a ser observada.
Outro aspecto a ser observado
é que o Lambda tentará automaticamente
repetir um lote de dados de streaming até obter êxito ou até
que os dados expirem.
Esse parece ser um ótimo recurso,
mas também pode causar problemas.
Portanto, se você não estiver lidando adequadamente com
os erros, isso poderá paralisar todo o fragmento, e
esse seria outro modo de falha do
qual você precisa estar ciente.
O que acontece se esse for o caso? Bem, usar mais
fragmentos pode ajudar a esclarecer esse caso.
Dessa forma, você pode garantir que seu processamento
não seja totalmente interrompido por erros quando eles forem encontrados.
Portanto, se você tiver um cenário em que
seu lote continua sendo repetido e um
erro continua ocorrendo, e como
isso está paralisando todo o seu pipeline, usar mais
shards é provavelmente uma maneira de corrigir esse erro.
Além disso, lembre-se de que o Lambda processa
dados de fragmentos de forma síncrona.
Ele não vai dividir esses dados e processá-los
em paralelo.
Portanto, você precisa pensar no tamanho
do lote, na quantidade de dados
que está enviando em um único lote e certificar-se
de que isso seja algo que uma
função Lambda processada de forma síncrona possa processar
em um curto espaço de tempo.
