Agora, vamos falar sobre o Amazon CloudWatch.
falar no CloudWatch é o CloudWatch Metrics.
Assim, o CloudWatch fornece
métricas para todos os serviços existentes no AWS e, portanto,
você pode monitorar tudo o que está acontecendo
em suas contas.
E uma métrica é apenas uma variável que você deseja monitorar.
Por exemplo, para uma instância
do EC2, poderia ser a CPUUtilization, a NetworkIn e assim por diante.
No caso do Amazon S3, pode ser o tamanho do seu balde e assim por diante.
Assim, as métricas pertencem a namespaces e, portanto,
são agrupadas em dois namespaces diferentes.
Basicamente, você tem um namespace por serviço.
Portanto, você tem dimensões,
e elas são atributos de uma métrica.
Por exemplo, uma métrica sobre CPUUtilization pode estar
relacionada a um ID de instância específico ou a um ambiente
específico, e assim por diante.
E você tem até 30 dimensões por métrica.
Portanto, as métricas são baseadas no tempo e,
por isso, devem ter um registro de data e hora.
E, depois que você tiver muitas métricas,
poderá criar um painel de métricas do CloudWatch para
que possa vê-las todas de uma vez, de maneira específica.
Além disso, você pode criar métricas personalizadas do CloudWatch.
Portanto, em vez de confiar nas métricas fornecidas
por todos os serviços do AWS, você pode criar sua própria
métrica personalizada.
Por exemplo, para extrair o uso de memória
de uma instância do EC2.
Esse é um caso clássico de uso de
uma métrica personalizada do CloudWatch.
Outra coisa que você pode fazer com suas métricas
do CloudWatch é transmiti-las para fora do CloudWatch.
Portanto, a ideia é que você queira transmitir continuamente
as métricas do CloudWatch para um destino de sua escolha.
Você terá uma entrega quase em tempo real e baixa latência.
E esse destino é o Amazon Kinesis Data Firehose e, a partir daí,
você pode enviá-lo para onde quiser.
Ou você também pode enviar suas métricas do CloudWatch
diretamente para um provedor de serviços de terceiros,
como Datadog, Dynatrace, New Relic, Splunk,
Sumo Logic e assim por diante.
Então, como isso funciona?
Bem, suas métricas do CloudWatch serão transmitidas quase em tempo
real para o Kinesis Data Firehose, e você obviamente
precisa configurar isso para que funcione.
E, a partir do Kinesis Data Firehose, é possível, por
exemplo, enviá-los para um bucket do Amazon S3, a partir do qual
você pode usar o Amazon Athena para analisar seus dados no Amazon S3, ou pode
usar o Amazon Redshift para ter um armazenamento
de dados para suas métricas, ou o Amazon OpenSearch
para criar painéis a partir do Amazon OpenSearch,
ou fazer análises lá.
E você pode optar por transmitir
todas as suas métricas para todos os namespaces
ou filtrar apenas alguns namespaces para que apenas um subconjunto
de suas métricas seja filtrado e
enviado ao Kinesis Data Firehose.
Agora vamos dar uma olhada no console.
Portanto, quando você está no painel do CloudWatch, no
lado esquerdo, há Métricas, e
você pode encontrar todas as métricas.
Agora, como você pode ver, vemos todos os namespaces
aqui para nossas métricas.
Se você der uma olhada, temos, com base nos serviços,
por exemplo, ELB, Auto Scaling, EBS, EC2, EFS e assim por diante.
Portanto, muitas informações são fornecidas a você aqui.
Assim, podemos clicar em EC2
e ter uma métrica por instância apenas
para ver uma métrica.
E vou digitar crédito
para ver o CPUCreditBalance, por exemplo.
Vou pegar essa
instância, que foi criada há muito
tempo, e vou escolher
um intervalo personalizado, que será
de um mês, para encontrar alguns dados aqui.
Temos os dados aqui.
Portanto, o mais legal com o CloudWatch
Metrics é que você pode simplesmente clicar
e selecionar o período de tempo desejado.
E aqui vamos nós, estamos obtendo algumas informações sobre
nossas métricas.
Portanto, como você pode ver, recebemos métricas a cada cinco minutos aqui.
Portanto, cada ponto de dados é a cada cinco minutos
porque o monitoramento detalhado não foi ativado para
essa instância, mas se eu
ativasse o monitoramento detalhado,
obteria dados a cada um minuto.
Esses são apenas os conceitos básicos do CloudWatch Metrics.
Nada muito sofisticado, mas podemos
definitivamente filtrar por tempo.
Podemos visualizá-lo como uma linha
diferente, ou seja, área empilhada, linha, número ou gráfico de pizza.
Você pode adicioná-lo a um painel.
Você pode baixá-lo em um arquivo . csv. Você pode compartilhá-lo, ok.
Portanto, o CloudWatch Metric é muito útil,
e você pode dar uma olhada em todas as métricas, com
base na região desejada, na dimensão
desejada, no ID do recurso desejado, para que possa
filtrar tudo.
Então é isso para o CloudWatch Metrics.
Espero que tenham gostado
e nos veremos na próxima palestra.
