o exame de Big Data.
Ainda assim, quero dar a você uma
visão geral, apenas uma nova atualização sobre o SQS.
Agora, você não precisa se lembrar de todos os detalhes.
Em geral, veremos as diferenças
entre o SQS e o Kinesis na próxima aula, mas você
só precisa ter uma compreensão geral de
como o SQS funciona.
Então, vamos dar uma olhada.
O SQS é uma fila e os produtores ou produtores ou produtores
enviarão mensagens para a fila do SQS e um consumidor
ou consumidores extrairão mensagens
dessa fila.
É basicamente assim que a fila funciona.
Isso parece muito semelhante ao Kinesis,
mas na verdade é muito, muito diferente.
Portanto, o SQS é a oferta mais antiga da AWS, com mais de 10 anos.
Ele é totalmente gerenciado,
e o SQS será dimensionado automaticamente de uma mensagem por segundo
até 15.000 mensagens por segundo, sem que você precise fazer nada.
O período de retenção padrão de uma mensagem é de quatro
dias, mas você pode ter um máximo de 14 dias, se desejar.
Não há limite para o número de mensagens que podem estar
na fila e a latência é extremamente
baixa, menos de 10 milissegundos para cada API de publicação e recebimento.
Há escalonamento horizontal em termos de número de consumidores,
de modo que você pode escalonar quantos consumidores
quiser e pode ter mensagens duplicadas com alta
taxa de transferência porque, ocasionalmente, você recebe
pelo menos uma entrega.
Você também pode ter mensagens fora de ordem,
portanto, não é uma ordenação tão boa quanto a do Kinesis,
e há uma ordenação de melhor esforço sendo feita.
Por fim, as mensagens precisam ser menores que as do Kinesis.
Há um limite de 1.024 kilobytes por mensagem enviada.
Agora, como produzimos mensagens?
Bem, as mensagens no Kinesis
têm um corpo e são feitas de uma cadeia de caracteres, ou seja,
são feitas de texto, e você pode adicionar atributos de metadados a elas.
Você pode adicionar pares de valores-chave basicamente
em cima dessa mensagem.
Você pode fornecer uma entrega com atraso, o que é opcional.
E, em seguida, essa mensagem é enviada ao SQS.
O que você recebe de volta é um ID de
mensagem e um hash MD5 do corpo, apenas para lembrar
o que você enviou ao SQS.
Portanto, ele é muito diferente do Kinesis.
Kinesis, lembre-se, estamos enviando bytes.
Aqui, estamos enviando uma string.
Kinesis, estamos tendo um tamanho máximo total de um megabyte.
Aqui, temos 256 kilobytes, certo?
Agora, consumindo mensagens, como fica?
Bem, os consumidores procuram mensagens
no SQS e podem receber até 10 mensagens
por vez, e precisam processar as mensagens
dentro do que é chamado de tempo
limite de visibilidade.
E, quando terminarem de processar a mensagem,
eles a excluirão da fila usando o ID da mensagem
recebida e o identificador
recebido.
Isso significa que, basicamente, quando você
tem o SQS, seus consumidores pesquisarão
as mensagens, processarão essas mensagens
e as excluirão da fila do SQS.
Portanto, as mensagens não podem ser processadas
por vários aplicativos de consumo diferentes.
Essa é uma diferença muito grande em relação ao Kinesis.
Portanto, lembre-se desse processo.
Os consumidores pesquisam as mensagens do
SQS, processam-nas e depois as excluem.
Agora, há um novo tipo de fila SQS.
Havia um QB4
padrão e agora há a fila FIFO ou FIFO.
E isso significa o primeiro a entrar, o primeiro a sair.
Ele não está disponível em todas
as regiões, mas acho que está quase lá.
E, basicamente, o nome da fila deve
terminar em . fifo para indicar que se trata de uma fila FIFO
e você terá uma taxa de transferência menor.
Agora, você tem limites.
Você recebe até 3.000 mensagens por segundo com batching ou 300 por segundo
sem batching, portanto, a taxa de transferência
é definitivamente menor.
Mas o que você obtém é que as mensagens
são processadas em ordem pelos seus consumidores.
Portanto, o primeiro a entrar é o primeiro a sair.
As mensagens serão enviadas exatamente uma
vez, e você terá um intervalo de deduplicação
de cinco minutos se enviar algo chamado
ID de duplicação.
Portanto, trata-se de um caso de uso diferente.
Menor taxa de transferência, mas mais
garantias sobre os pedidos, se você precisar disso.
A fila FIFO funciona de modo que, se suas mensagens
forem enviadas uma, duas, três, quatro,
cinco, elas também serão lidas na ordem, uma,
duas, três, quatro, cinco, por seus consumidores.
Então, como enviamos mensagens grandes no SQS?
Não é realmente recomendado,
mas há algo chamado cliente estendido SQS, que é uma
biblioteca Java que usa um truque.
Basicamente, ele usará um bucket do Amazon S3 como companheiro,
e diremos, ok, vou enviar
a carga útil muito grande, talvez como
10 gigabytes ou cinco, ou você sabe,
cinco megabytes ou 10 megabytes para o S3,
e ele enviará uma mensagem de metadados na fila do SQS.
E, em seguida, o cliente de extensão
no lado do consumidor receberá a pequena mensagem de
metadados informando onde o arquivo está no S3, e o consumidor
poderá ler a mensagem grande diretamente do S3.
Portanto, é assim que você contorna o
limite de mensagens de 256 kilobytes, se quiser, usando
os clientes estendidos do SQS, o que
pode ser muito útil para big data.
Agora, os casos de uso do SQS serão para desacoplar aplicativos.
Por exemplo, se você quiser tratar pagamentos de forma assíncrona ou gravações
em buffer em um banco de dados.
Por exemplo, se você tem um aplicativo
de votação, espera um pico de rendimento e precisa
ser capaz de escalonar muito rapidamente ou lidar
com grandes cargas de mensagens que chegam, por exemplo, se
você tiver um remetente de e-mail.
O SQS também pode ser integrado ao dimensionamento automático
por meio do CloudWatch se você tiver instâncias do
EC2 lendo a partir da fila do SQS.
E quanto aos limites?
Bem, você tem um máximo de 120.000 mensagens em voo processadas
pelos consumidores de cada vez.
A solicitação em lote só pode extrair até 10 mensagens.
O conteúdo da mensagem é texto, portanto,
deve ser XML, JSON ou apenas texto.
E a fila padrão em si, no entanto,
tem transações ilimitadas e ilimitadas por segundo.
Portanto, você pode ter o máximo de mensagens
por segundo em termos de taxas de transferência para o SQS.
A fila FIFO, a fila FIFO, no entanto, suporta
até 3.000 mensagens por segundo usando lotes.
Portanto, lembre-se disso.
E o tamanho máximo da mensagem é de 1.024 kilobytes.
Se precisar de mais, você pode usar o cliente estendido.
O período de retenção de dados pode variar de
um minuto a 14 dias, mas lembre-se de que, depois de lidas,
as mensagens são excluídas da fila do SQS.
Em termos de preço, ele é muito diferente do Kinesis.
Você pagará por solicitação de API
e pagará pelo uso da rede ou fará o mesmo.
Agora, em termos de segurança do SQS, em que
obtemos a criptografia SSL em voo, se usarmos
o ponto de extremidade HTTPS para o SQS, que é o padrão, e podemos ter criptografia
do lado do serviço usando o KMS, por exemplo, podemos
definir a chave mestra que queremos usar.
E o SSE, o KMS, criptografará diretamente o corpo da mensagem que
enviamos ao SQS, mas não os metadados em si.
Portanto, o carimbo de data e hora do
ID da mensagem e os atributos não serão criptografados
pela criptografia do lado do servidor.
A política de IAM deve permitir o uso do SQS.
Portanto, é possível definir qual usuário pode enviar dados para qual fila e,
além disso, podemos definir uma política de acesso à fila do SQS
se quisermos restringir ainda mais a segurança.
Ele pode obter um controle mais preciso, por exemplo, sobre o IP.
Ou podemos controlar o tempo e as solicitações que chegam.
Então é isso para o SQS. Apenas uma visão geral de alto nível.
Você não precisa se lembrar de todos
esses detalhes que acabei de lhe dar.
Lembre-se apenas da ideia geral, dos limites e de todas essas coisas.
Espero que tenha sido útil e, na próxima
aula, vamos comparar os fluxos de dados do Kinesis e do SQS.
Então, vejo você na próxima palestra.
