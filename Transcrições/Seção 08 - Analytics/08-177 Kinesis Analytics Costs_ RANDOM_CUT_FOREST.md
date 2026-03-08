Ele é sem servidor.
Portanto, você paga apenas pelos recursos que consome e nada mais.
Ele é dimensionado para você automaticamente, e você não precisa se preocupar com os recursos subjacentes
necessários para executar os aplicativos do Kinesis Analytics.
No entanto, ele não é barato, ao contrário de outros serviços sem servidor que a AWS oferece.
Quando eu estava criando este curso, o Kinesis Analytics, na verdade, representou a maior parte dos
custos reais em que incorri ao desenvolver este curso.
Portanto, use-o com cuidado e certifique-se de encerrar todos os trabalhos de análise quando terminar de usá-los.
Só para garantir.
No que diz respeito à segurança, você pode usar as permissões do IAM para acessar os serviços de streaming, origem
e destino com os quais está trabalhando, de modo que possa configurar o IAM para permitir que o aplicativo Kinesis Analytics se comunique
com quaisquer serviços upstream e downstream com os quais precise se comunicar.
Há também um recurso interessante no Kinesis Analytics chamado Schema Discovery, que é como os nomes das colunas em
seu SQL são encontrados.
Na verdade, ele pode analisar os dados recebidos do seu fluxo enquanto você o configura.
Assim, você pode verificar se funcionou, mas é muito legal.
Na verdade, ele pode analisar um fluxo de entrada e escrever no console do AWS.
Você pode ver como ele está tentando dar sentido a esses dados e transmitir um esquema sobre eles, e pode editar e
corrigir esses dados conforme necessário.
Também vale a pena falar sobre algo chamado floresta de corte aleatório.
Essa é uma função SQL oferecida pelo Kinesis Data Analytics que pode ser usada em seu aplicativo
de análise de dados para detecção de anomalias em qualquer coluna numérica de um fluxo.
E dá para perceber que a AWS está muito orgulhosa disso, pois publicou um artigo inteiro sobre o assunto,
que você pode consultar se quiser.
É uma nova maneira de identificar exceções em um conjunto de dados para que você possa lidar com elas da maneira que precisar.
Um exemplo de como fazer isso que eles dão no artigo é detectar o número anômalo de passageiros no metrô durante
a Maratona de Nova York.
Portanto, eles têm um fluxo de dados de pessoas que passam pelas catracas do metrô e estão usando
uma floresta de corte aleatório para identificar automaticamente anomalias nessa taxa de uso do sistema de metrô.
Isso é importante porque, se você tiver uma pergunta sobre a tentativa de detectar anomalias ou discrepâncias
em um fluxo de dados, a floresta de corte aleatório com o Kinesis Analytics provavelmente será uma boa resposta para isso.
