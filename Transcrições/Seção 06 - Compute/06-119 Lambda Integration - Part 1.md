Por que não executá-lo em um servidor?
Bem, embora o Lambda ainda esteja sendo executado em servidores sob o capô, eles não são servidores que
você gerencia, e isso é um grande problema.
Portanto, a Amazon tem pessoas com pagers para manter esses servidores funcionando e lidar com todos os patches, monitoramento,
falhas de hardware e outras coisas.
Portanto, você não precisa pensar nisso quando estiver executando o AWS Lambda.
Tudo o que você pensa é no código que está sendo executado nele.
E, sim, embora os servidores individuais possam ser baratos, o escalonamento desses servidores pode ficar muito
caro rapidamente.
E se você escalar uma frota para executar sua função para gerenciar sua capacidade de pico, acabará pagando por muito
tempo de processamento que nem sequer está usando quando está fora do pico.
Com o Lambda, você só paga pelo tempo de processamento que está realmente consumindo, o que pode ser enorme
do ponto de vista da economia de custos.
E, embora isso não seja tão importante no mundo do big data, se você estiver lidando com algo como um
site sem servidor, será mais fácil dividir seu desenvolvimento entre desenvolvimento front-end e desenvolvimento
back-end.
Assim, enquanto o trabalho de back-end pode ser realizado em suas funções Lambda, os desenvolvedores de front-end se
preocupam com todas as coisas estáticas no site do cliente de front-end.
Portanto, há vários usos principais do lambda.
Um deles é o processamento de arquivos em tempo real.
Assim, à medida que novos dados chegam ao S3 ou a algum outro destino no AWS, o Lambda pode ser acionado e processar
esse arquivo como você quiser.
E isso pode incluir a realização de um ETL rudimentar, ou seja, extrair, transformar e carregar.
Portanto, o Lambda é apenas código.
Você pode fazer o que quiser lá dentro.
E isso inclui a realização de ETL nos dados recebidos.
Você também pode fazer processamento de fluxo em tempo real.
Conforme discutimos, basta ouvir os novos eventos que chegam em um fluxo do Kinesis Stream ou do Kinesis Firehose.
Você também pode usar o Lambda como um substituto do cron.
E isso é interessante.
Você também pode usar o tempo como um acionador para a função lambda.
Assim, da mesma forma que você pode acionar eventos usando o cron em um sistema Linux, também pode acionar eventos
lambda em uma programação fixa.
Portanto, se você precisar que algo aconteça uma vez por dia, uma vez por hora, uma vez por minuto
ou qualquer programação que desejar, poderá configurá-la para chamar a função Lambda periodicamente,
o que pode ser útil para iniciar trabalhos diários em lote ou algo assim.
Além disso, ele pode processar eventos arbitrários dos serviços da AWS.
E, como veremos, há uma longa lista de serviços da AWS que podem gerar acionadores para o Lambda.
Praticamente qualquer linguagem em que você queira desenvolver é compatível com o Lambda, o que é ótimo.
Nó. js, Python, Java C sharp.
Go, PowerShell, Ruby.
Assim, você pode processar dados e fazer o que quiser com eles em praticamente qualquer linguagem que desejar.
E isso é muito importante, porque significa que qualquer sistema que tenha uma interface em qualquer uma dessas linguagens
é um jogo justo para o seu código Lambda.
Portanto, lembre-se do código lambdas.
E, com o código, tudo é possível.
Portanto, você não precisa se limitar a servir apenas como uma cola ou uma transformação entre diferentes
serviços da AWS.
Na verdade, você pode conversar com outros serviços fora da AWS, se quiser, ou com outras bibliotecas que
possam permitir que você realize transformações mais interessantes nesses dados.
Portanto, você pode realmente usar sua imaginação quando estiver usando o Lambda para fazer muitas coisas diferentes.
Ele realmente possibilita muitas coisas, tudo sem gerenciar servidores no processo, o que é fantástico.
Agora, se você estiver usando o Lambda para servir como uma espécie de cola entre os serviços da AWS, há uma longa lista
de serviços aqui que realmente acionam eventos do Lambda para você.
Portanto, qualquer um desses serviços pode disparar gatilhos para funções Lambda sempre que algo interessante
acontecer nesses serviços.
E esta é apenas uma lista parcial deles.
O mesmo acontece com a Alexa.
Além disso, você também pode fazer invocações manuais com as funções Lambda.
Vamos destacar alguns dos mais comuns que são relevantes para o big data.
E isso seria S3, Kinesis, DynamoDB, SNS e SQS e IoT.
Assim, você pode integrar o Lambda com o S3.
Portanto, sempre que algo predefinido acontece com um objeto no S3, isso pode atuar como um dado de evento que invocará
uma função lambda.
Assim, por exemplo, um novo objeto é criado no S3.
Você pode ter um acionador lambda que capta a criação desse objeto, dá a volta, analisa
essas informações e as coloca no redshift ou algo assim.
A mesma história com o DynamoDB.
Toda vez que algo é alterado em uma tabela do DynamoDB, isso pode acionar dados de eventos que também invocam uma
função Lambda, o que permite o processamento de dados em tempo real e orientado por eventos para
os dados que chegam às tabelas do DynamoDB. Você pode integrar o Lambda com o Kinesis Streams e, em seguida, a função lambda pode
ler registros de um fluxo e ser processada de acordo.
Agora, sob o capô, o Lambda está realmente puxando o fluxo do Kinesis.
O fluxo não está enviando dados para o lambda.
Essa pode ser uma distinção importante em alguns contextos.
Portanto, lembre-se de que, quando você tem fluxos do Kinesis, falar com o Lambda Kinesis não é realmente empurrar esses dados
para o lambda, como os diagramas de arquitetura podem sugerir.
Na verdade, o Lambda extrai esse fluxo periodicamente e coleta informações dele em lote.
Você também pode integrar o Lambda à IoT.
Assim, quando algum dispositivo começa a enviar dados para o serviço de IoT, ele pode invocar o Lambda e processá-los
de acordo com a definição de sua função lambda, e ele se integra ao Kinesis Firehose.
Nesse caso, o Lambda pode transformar os dados e fornecer esses dados transformados para o S3, Redshift,
Elasticsearch ou o que você quiser.
Ele pode gerar praticamente qualquer coisa, porque você pode escrever código para fazer o que quiser.
Em resposta a esses acionadores.
Todos os serviços do AWS têm APIs que você pode chamar.
Portanto, na verdade, o céu é o limite para o que você pode chamar a jusante de sua função Lambda.
Você pode fazer o que quiser.
Esses são apenas os que podem acionar uma função lambda para você automaticamente.
