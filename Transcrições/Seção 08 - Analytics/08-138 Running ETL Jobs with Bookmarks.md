há algumas maneiras de fazer isso.
Novamente, uma delas é usar um agendamento baseado em tempo no estilo Cron,
portanto, se você precisar executá-lo em algum tipo de agendamento
fixo, poderá fazer isso, no mesmo formato do Cron, ou
pode ter algo chamado marcadores de trabalho.
Novamente, esse é um aspecto importante para o exame.
Portanto, um marcador de trabalho é usado para manter o estado da execução do trabalho.
Portanto, se você precisar configurar
as coisas para não acabar reprocessando os mesmos dados, um marcador
permite que você acompanhe de onde parou, de modo que possa evitar
o reprocessamento de dados antigos e apenas processar
esses novos dados quando for executado novamente em uma programação.
Portanto, o marcador de trabalho mantém o controle de onde você parou quando
estiver executando os trabalhos do Glue em uma programação.
Ele funciona com fontes S3 em vários formatos e
também pode funcionar com bancos de dados relacionais via JDBC
se suas chaves primárias estiverem em ordem sequencial.
Agora, esse recurso só lida com novas linhas, não com linhas atualizadas.
Portanto, você só pode usar marcadores de trabalho com um banco de dados relacional
se estiver injetando novos dados como novas linhas.
Se ele estiver voltando e atualizando as linhas existentes,
os marcadores de trabalho não funcionarão da maneira esperada.
Pode ser importante saber disso.
Também eventos do CloudWatch.
Assim, você pode disparar uma função Lambda
ou uma notificação SNS, o que quiser, quando um trabalho
de ETL no Glue for bem-sucedido ou falhar.
Portanto, o Glue se integra ao CloudWatch para acompanhar
o que aconteceu e, possivelmente,
notificá-lo com base em eventos encadeados por meio de SNS ou
Lambda, o que você quiser fazer, quando o trabalho for
bem-sucedido ou falhar.
Quando isso acontece, você pode invocar uma execução
do EC2 para fazer um processamento adicional, enviar o evento para o Kinesis,
ativar uma função de etapa, o que você quiser fazer.
Portanto, lembre-se de que, usando
o CloudWatch, você pode associar o Glue
a outros sistemas, como EC2, Kinesis ou AWS Step Functions.
