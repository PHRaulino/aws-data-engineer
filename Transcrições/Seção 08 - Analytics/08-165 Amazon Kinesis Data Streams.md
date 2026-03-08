Então, o primeiro serviço que você precisa
E o Kinesis Data Streams é uma
maneira de transmitir big data em seus sistemas.
Portanto, um fluxo de dados do Kinesis é composto
de vários fragmentos, e os fragmentos
são numerados.
Número um, número dois, até o número N.
E isso é algo que você precisa providenciar com antecedência.
Portanto, quando você começa a usar o Kinesis
Data Streams, está dizendo: "Quero um fluxo com seis shards".
Assim, os dados serão divididos em todos os fragmentos.
Está bem?
E os fragmentos definirão sua capacidade de fluxo
em termos de taxas de ingestão e consumo.
Então, por enquanto, vamos começar com isso.
E depois temos os produtores.
Portanto, os produtores enviam dados para os fluxos de dados do Kinesis, e os
produtores podem ser múltiplos.
Eles podem ser aplicativos,
podem ser clientes de desktop ou clientes móveis,
podem estar aproveitando o AWS SDK em um nível muito,
muito baixo, ou a Kinesis Producer Library, KPL,
em um nível mais alto, e vamos nos aprofundar
nos produtores nas próximas palestras, ou pode ser o Kinesis
Agent dentro do servidor para transmitir,
por exemplo, logs de aplicativos para o
Kinesis Data Streams.
Portanto, todos esses produtores fazem exatamente a mesma coisa.
Eles dependem do SDK em um nível muito, muito baixo, e vão
produzir registros
em nosso Kinesis Data Stream.
Portanto, um registro, em sua essência, é composto por
duas coisas: é composto por uma chave de partição e é composto
pelo blob de dados ou pelo valor de até um megabyte.
Portanto, a chave de partição definirá
e ajudará a determinar para qual fragmento o registro irá.
E o blob de dados é o próprio valor.
Portanto, quando os produtores enviam dados
para o Kinesis Data Streams, eles podem enviar
dados a uma taxa de um megabyte por segundo,
ou mil mensagens por segundo, por fragmento.
Portanto, se você tiver seis fragmentos, terá
seis megabytes por segundo, ou 6.000 mensagens por segundo, no total, certo?
Agora, uma vez que os dados estejam no Kinesis Data Streams,
eles podem ser consumidos por muitos consumidores, e esses
consumidores, mais uma vez, podem ter muitas formas,
e vamos explorá-las em detalhes nesta seção.
Portanto, temos aplicativos e eles
podem depender do SDK ou, em um nível mais alto, das bibliotecas de clientes
Kinesis, ou seja, KCL. Elas podem ser funções Lambda, se você
quiser fazer o processamento sem servidor com base
no Kinesis Data Streams.
Pode ser o Kinesis Data Firehose,
como veremos nesta seção,
ou o Kinesis Data Analytics.
Portanto, quando o consumidor recebe um registro,
ele recebe, novamente, a chave de partição, também
um número de sequência que representa onde o registro estava no fragmento,
bem como o blob de dados, ou seja, os próprios dados.
Agora temos diferentes modos de
consumo para o Kinesis Data Streams.
Temos dois megabytes por segundo de taxa de transferência
compartilhada para todos os consumidores, por fragmento, certo?
Ou você obtém dois megabytes por segundo, por fragmento, por consumidor,
se estiver habilitando o modo de consumidor aprimorado, o fan-out
aprimorado.
Portanto, nesta seção, analisaremos isso novamente
com mais detalhes.
Então, novamente, os produtores enviam dados para o Kinesis Data Streams.
Ele permanece lá por um tempo e depois é lido
por muitos consumidores diferentes.
Algumas propriedades do Kinesis Data Streams.
A primeira é que a retenção pode
ser definida entre 1 dia e 365 dias.
E isso significa que, por padrão,
você tem a capacidade de reprocessar ou reproduzir dados.
E uma vez que os dados são inseridos no Kinesis, eles
não podem ser excluídos.
Isso é chamado de imutabilidade.
Além disso, quando você envia mensagens para o Kinesis Data Streams,
adiciona uma chave de partição. E as mensagens que compartilham
a mesma chave de partição irão para o mesmo fragmento,
o que lhe dá uma ordenação baseada em chave.
Para produtores, você pode enviar dados usando o
SDK, a Kinesis Producer Library, KPL ou os Kinesis Agents.
E para os consumidores, você pode escrever o seu próprio.
Portanto, a Kinesis Client Library, KCL, ou o SDK, ou você
pode usar um consumidor gerenciado no AWS,
como o AWS Lambda, o Kinesis Data Firehose
ou o Kinesis Data Analytics.
Agora, com relação aos modos de
capacidade, você tem duas opções para o Kinesis Data Stream.
O primeiro, que é o modo de capacidade histórica,
é chamado de modo provisionado.
Assim, você escolhe um número de shards provisionados
e pode dimensioná-los manualmente ou usando uma API.
E cada shard no Kinesis Data Streams
receberá um megabyte por segundo, ou
1.000 registros por segundo.
E, em seguida, para a taxa de transferência, cada
fragmento receberá dois megabytes por segundo,
e isso se aplica ao consumidor clássico ou fan-out.
Você também paga por shard provisionado por hora.
Portanto, você precisa pensar com bastante antecedência,
e é por isso que ele é chamado de modo provisionado.
Mas o segundo modo é um modo neuro chamado modo On-demand.
E, nesse caso, você não precisa provisionar
ou gerenciar a capacidade.
Isso significa que a capacidade será ajustada
ao longo do tempo, sob demanda.
Você obtém a capacidade padrão provisionada,
que é de quatro megabytes por segundo, ou 4.000 registros por, e depois
haverá um dimensionamento automático com base
no pico de throughput observado nos últimos 30 dias.
E, nesse modo, você ainda pagará
por streaming por hora e por entrada/saída de dados por gigabyte.
Portanto, um modelo de preços diferente.
Portanto, se você não conhece seus eventos de capacidade, opte pelo On-demand,
mas se puder planejar os eventos de
capacidade, opte pelo modo Provisioned.
Em termos de segurança para o Kinesis Data Streams,
ele é implantado em uma região.
E assim você tem seus fragmentos.
Você pode controlar o acesso para produzir e ler a partir do
fragmento usando políticas de IAM.
Há criptografia em voo usando HTTPS e criptografia
em repouso usando KMS.
Você pode implementar sua própria criptografia e descriptografia
de dados no lado do cliente, o que é chamado de
criptografia do lado do cliente, e é
mais difícil de implementar porque você mesmo precisa
criptografar e descriptografar os dados.
Mas isso aumenta a segurança.
Os pontos de extremidade VPC estão disponíveis para o Kinesis.
Isso permite que você acesse o Kinesis diretamente
do HTTPS, por exemplo, em um
assunto privado, sem passar pela Internet.
E, por fim, todas as chamadas
de API podem ser monitoradas usando o CloudTrail.
Então é isso para uma visão geral do Kinesis Data Streams.
Espero que você tenha gostado.
E eu o verei na próxima palestra para um mergulho mais
profundo em todas as partes móveis do Kinesis Data Streams.
