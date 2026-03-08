Portanto, vamos dedicar um pouco de tempo para falar sobre isso em detalhes.
É um ponto de extremidade HTTP seguro para instruções SQL em seu cluster redshift.
E isso pode ser um cluster provisionado ou um cluster sem servidor.
E isso pode lidar com consultas individuais e em lote.
Portanto, ele oferece, entre outras coisas, um endpoint Rest que pode ser integrado aos seus próprios aplicativos.
E é isso que estamos ilustrando aqui na parte inferior da tela.
Assim, você pode ter usuários conversando com algum aplicativo que você criou.
Esse aplicativo pode, então, passar pelo AWS SDK e chamar a API de dados do Amazon Redshift por meio dele e, por meio
dessa API, executar consultas no cluster do Redshift, onde quer que ele esteja.
Assim, você pode usar isso fora do AWS.
Potencialmente, ele é assíncrono.
Portanto, você fará uma chamada para solicitar uma consulta em um lote ou uma consulta individual.
E, em seguida, você precisa fazer outra chamada com o identificador que ele lhe devolve para
recuperar os resultados mais tarde.
Ele não exige o gerenciamento de conexões como em um banco de dados normal, portanto, você não precisa
se preocupar em ter os drivers corretos instalados no seu aplicativo ou algo do gênero.
Tudo isso é abstraído de você por meio da API de dados.
E, do ponto de vista da segurança, você não precisa se preocupar.
As senhas também não são enviadas por meio da API.
Ele usa o AWS Secrets Manager para gerenciar credenciais ou você pode configurar credenciais temporárias no
redshift para o seu aplicativo.
De qualquer forma, a senha não é enviada pelo cabo como parte da API e, como ela pode ser invocada pelo SDK do AWS,
isso significa que você pode acessar o redshift por meio de qualquer linguagem compatível com o SDK, que
inclui C plus plus, go, Java, JavaScript.
Net, Node. js, PHP, Python e Ruby.
E, como na maioria dos serviços, ele se integra ao CloudTrail.
Portanto, se você precisar monitorar o que está acontecendo ou arquivar o que está sendo executado por meio dessa API, o CloudTrail
poderá capturar essas chamadas de API para você e armazená-las no S3 em algum lugar.
E não se trata apenas de integração de aplicativos.
Ele também se integra a muitos outros serviços do ecossistema da AWS.
E todos eles são visualizados aqui à direita.
Portanto, como eu disse, podemos usar o endpoint Rest para integrá-lo ao seu próprio aplicativo.
Foi sobre isso que conversamos.
Mas você também pode integrá-lo a uma variedade de outros serviços.
E uma muito popular seria usar o AWS Step Functions junto com a API de dados do Redshift para orquestrar um processo
de ETL, extrair, transformar e carregar.
Portanto, se você quiser configurar um fluxo de trabalho de processamento de dados usando funções de etapa, poderá chamar
a API de dados do Redshift como parte desse fluxo de trabalho e configurar um pipeline de ETL orientado por eventos usando a API de dados.
Você também pode acessar o Redshift Data API por meio de um notebook do SageMaker.
Portanto, se você precisar usar o redshift de um notebook SageMaker, também poderá fazer isso.
E ele também se integra ao Amazon EventBridge.
E esse é um aspecto importante no contexto da engenharia de dados.
Portanto, você pode transmitir dados da API de dados para outro local usando o EventBridge, monitorando os dados que
saem da API de dados.
Assim, você poderia, por exemplo, transmitir esses dados de um aplicativo para o Lambda usando o EventBridge.
Para fazer isso, basta definir o parâmetro de evento width como true.
Para realizar esse tipo de streaming, você também pode programar operações de API de dados usando o EventBridge.
Portanto, o EventBridge pode ser usado para agendar operações em um cronograma consistente ou em resposta a algum outro
tipo de evento.
Portanto, a API de dados do EventBridge Plus é algo que você deve conhecer sobre alguns pontos mais finos do uso da
API de dados.
Portanto, há uma série de limites máximos sobre o que você pode fazer com ele.
E, por padrão, a duração da consulta pode durar apenas 24 horas.
Você só pode ter 500 consultas ativas por vez.
O tamanho do resultado, que é compactado em gzip, só pode ser de até 100 MB.
O resultado será mantido por apenas 24 horas.
Portanto, se você não conseguir obtê-lo após um dia inteiro, ele desaparecerá.
O tamanho do comando da consulta só pode ser de 100 KB, e o próximo é um pouco mais importante do que o pacote para
o tamanho da consulta.
Isso significa que a quantidade de dados por linha em seus resultados é de 64 KB.
Portanto, se você receber uma mensagem de erro da sua chamada à API de dados dizendo que o pacote para
consulta é muito grande, isso significa que há muitas informações por linha nos dados que você está
recuperando, e esse limite máximo é de 64 KB.
Além disso, há um tempo máximo de retenção de oito horas para tokens de cliente para acessar a
API, e há várias cotas de TPS por chamada de API.
Por exemplo, para executar a instrução.
Você está limitado a 30 transações por extrato.
Falando em chamadas de API, estas são as que estão disponíveis para você.
Há o comando execute para executar um único comando SQL ou o comando batch execute para executar vários comandos
de uma só vez.
Depois de enviar essa declaração, você pode descrever a declaração ou a tabela por trás dela.
E, novamente, isso é síncrono.
Portanto, quando você chamar uma chamada de instrução de execução ou uma chamada de instrução de execução em lote,
ela apenas devolverá um identificador, não o resultado real.
Então, você precisa voltar e passar esse identificador de volta para o resultado da instrução get para recuperar posteriormente
o resultado dessa consulta.
Você também pode cancelar um extrato que esteja em andamento usando cancelar extrato com o mesmo ID.
E há alguma segurança para garantir que você não possa bisbilhotar as consultas de outras pessoas.
Portanto, você precisa ter a mesma função ou permissão de IAM para operar em uma determinada declaração ao executar e obter a declaração,
o resultado ou o que quer que seja.
Portanto, você não pode obter o resultado de uma chamada de instrução para a chamada de instrução de execução de outra pessoa, por exemplo.
Obviamente, o cluster também deve estar em uma VPC.
Portanto, a menos que seu cluster redshift esteja em uma nuvem privada virtual, ele não funcionará.
