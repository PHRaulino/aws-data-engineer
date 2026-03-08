fan-out SNS + SQS.
A ideia é que você queira que uma mensagem seja
enviada para várias filas do SQS.
Mas se você enviá-los individualmente para cada fila do SQS, pode haver
problemas associados a eles.
Por exemplo, se o aplicativo falhar no meio,
se houver falhas de entrega ou
se você adicionar mais filas SQS no futuro.
Portanto, queremos usar o padrão fan-out.
A ideia é que você faça o push uma vez no tópico do SNS
e, em seguida, assine
quantas filas do SQS quiser no tópico do SNS.
Essas filas são assinantes
e todas elas receberão as mensagens enviadas para o SNS.
Assim, por exemplo, temos
um serviço de compras que deseja enviar
mensagens para duas filas SQS.
Em vez disso, ele
enviará uma mensagem para um tópico do SNS, e
as filas serão assinantes desse tópico do SNS para que
o serviço de fraude e o serviço de envio possam
ler todas as mensagens de suas próprias filas do SQS.
A ideia com isso também é que
se trata de um modelo totalmente desacoplado e não há perda de dados.
O SQS lhe dará persistência de dados, processamento atrasado
e novas tentativas de trabalho.
E, com esse padrão, podemos adicionar mais filas SQS
como assinantes do tópico SNS ao longo do tempo.
Para isso, precisamos nos
certificar de que a política de acesso à fila do SQS, como
vimos anteriormente, permita que o tópico do SNS grave nas filas do SQS.
Portanto, novamente, mais um
caso de uso de políticas de acesso à fila.
E temos entregas em várias regiões.
Portanto, é definitivamente possível que um tópico SNS
em uma região envie mensagens para filas SQS em outras regiões,
se a segurança permitir.
Próximo. Então, como podemos usar esse padrão para outros fins?
Por exemplo, eventos S3 em várias filas.
Portanto, há uma limitação das regras de eventos do
S3: para uma combinação de tipos de eventos.
Por exemplo, se um objeto estiver sendo
criado e um prefixo, por exemplo, images/,
você só poderá ter uma regra de evento S3.
Mas e se você quiser enviar a mesma notificação de evento do
S3 para várias filas do SQS?
Nesse caso, você usaria o padrão fan-out.
Assim, por exemplo, temos um objeto S3 criado como
um evento que aparece em seu bucket S3.
Enviaremos esse evento para um tópico do SNS e assinaremos
muitas filas do SQS para o tópico do SNS como
um padrão de fan-out.
Mas também poderíamos assinar outro tipo de aplicativo,
e-mail, funções Lambda, etc., etc.
E o que obtemos com
isso é que a mensagem do evento que está acontecendo no Amazon S3
vai para muitos destinos diferentes.
Graças a esse padrão em leque.
Outra arquitetura é que você pode enviar dados diretamente
do SNS para o Amazon S3 por meio do Kinesis
Data Firehose.
Portanto, como o SNS tem uma integração direta com o KDF, seu serviço
de compra pode enviar dados para um tópico do SNS.
Em seguida, o Kinesis Data Firehose,
KDF, receberá essas informações.
E, a partir do Kinesis Data Firehose,
você pode enviá-lo para seus buckets do Amazon S3.
Ou, nesse caso, qualquer destino específico do KDF suportado que permita
que você seja realmente extensível
na maneira como deseja persistir as mensagens
do tópico do SNS.
Portanto, também podemos aplicar o padrão de fan-out aos tópicos FIFO.
Portanto, o Amazon SNS tem um recurso FIFO ou FIFO, que é o primeiro a entrar, primeiro
a sair, o que permite ordenar
as mensagens no tópico.
Portanto, o produtor envia as mensagens um, dois, três, quatro,
e os assinantes só podem ser uma fila SQS FIFO por enquanto, que está recebendo
as mensagens um, dois, três, quatro, em ordem.
Portanto, a ideia é que, com o SNS FIFO, obtenhamos
os mesmos recursos do SQS FIFO, ordenando
por ID de grupo de mensagens.
Obtemos a deduplicação usando um ID de deduplicação ou
a deduplicação baseada em conteúdo.
E tanto as filas padrão SQS quanto as filas FIFO podem ser assinantes.
Em termos de taxas de transferência, você está limitado.
Você obtém as mesmas taxas de transferência que a fila SQS FIFO
porque, no momento, somente as filas SQS
FIFO podem ler dos tópicos SQS FIFO.
Então, por que precisamos disso?
Bem, caso você queira fazer um fan-out usando o SQS FIFO.
Portanto, você precisa de fan-out, ordenação e deduplicação.
Portanto, o serviço de compra
enviará os dados para um tópico
FIFO do SNS e, em seguida, para duas filas FIFO do SQS, que também
podem fazer com que o serviço
de fraude e o serviço de remessa leiam das filas FIFO.
Um último recurso do SNS que pode ser muito útil
em relação ao padrão de fan-out
é que você pode filtrar as mensagens no SNS.
Então, o que é filtragem de mensagens?
Bem, trata-se de uma política JSON usada para filtrar
mensagens enviadas para a assinatura do tópico do SNS.
Portanto, se uma assinatura não tiver uma política de filtro,
ela receberá todas as mensagens, e esse é o comportamento padrão.
Mas vamos dar um exemplo
do que acontece quando configuramos uma política de filtragem de mensagens.
Portanto, temos um serviço de
compras e ele envia transações para um tópico do SNS.
Por exemplo, a transação parece
ter um número de pedido,
um produto, por exemplo, um
lápis, a quantidade e os estados em que foi colocado.
Agora, queremos criar uma fila SQS apenas para os pedidos feitos.
Não todos os pedidos, mas apenas os pedidos feitos.
Para isso, assinaremos a fila do SQS no
tópico do SNS, aplicaremos
uma política de filtro em JSON e especificaremos
em uma política que queremos
que os estados sejam iguais.
Assim, somente as mensagens que corresponderem à política
entrarão na fila do SQS.
Mas então podemos ter uma fila SQS para pedidos cancelados.
Assim, podemos criar nossa própria política de filtro
para pedidos cancelados e fazer com
que os pedidos provenientes do mesmo tópico do SNS
entrem na fila do SQS.
Portanto, a fila SQS de pedidos feitos e de pedidos cancelados
não terá as mesmas mensagens.
Também podemos usar a mesma política
de filtro, a cancelada,
para criar uma assinatura de e-mail para pedidos cancelados.
Poderíamos ter uma política de filtro
para pedidos recusados, por exemplo, e como outra fila do SQS, ou podemos
criar uma fila do SQS sem uma política de filtro para receber
todas as mensagens desse tópico do SNS.
Assim, usando todos esses padrões de fan-out e filtragem de mensagens,
filas FIFO e tópicos FIFO, obtemos
muitas possibilidades diferentes e o exame.
Tentaremos testá-lo em todos eles.
Então é isso para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
