Muito bem, agora vamos falar sobre
os modos de capacidade de leitura e gravação do DynamoDB.
Portanto, é assim que você controla a capacidade da sua mesa.
Portanto, você precisa especificar antecipadamente a taxa de transferência
de leitura e gravação.
Portanto, na verdade, você tem dois modos.
O primeiro é chamado de modo provisionado, no qual
especificamos a leitura e as gravações por segundo, também chamadas de unidade
de gravação.
Portanto, é preciso planejar sua capacidade com antecedência.
Você pagará pelo que for provisionado.
Portanto, se você disser que quero 10 unidades de capacidade
de leitura e cinco unidades de capacidade
de gravação, você pagará por isso a cada hora.
E você tem a opção de fazer o dimensionamento
automático, como veremos em breve.
Há um segundo modo chamado de modo sob demanda.
E esse terá automaticamente as leituras e gravações escaladas
para cima e para baixo com base em suas cargas de trabalho.
E não há necessidade de planejamento de capacidade.
Portanto, você não precisa provisionar unidades de capacidade.
Eles simplesmente estarão lá.
E você pagará exatamente pelo que usar.
Mas isso será muito mais caro do que
o modo provisionado.
Portanto, a ideia é que você tenha diferentes
casos de uso, e os veremos em detalhes nesta palestra.
Portanto, você pode alternar entre
os dois modos, provisionado e sob demanda, uma vez a cada 24 horas.
Portanto, vamos nos aprofundar em ambos.
Portanto, não se preocupe no momento. É apenas uma introdução.
Mas agora vamos nos aprofundar no modo de
capacidade de leitura provisionada.
Portanto, você deve provisionar unidades de capacidade de leitura
e gravação, também chamadas de RCU, que é a taxa de transferência
para leituras, e WCU, que é a taxa de transferência para gravações.
Agora, você tem a opção de configurar o dimensionamento automático da
taxa de transferência para atender à demanda.
Portanto, não pense muito sobre o valor de sua RCU
e de sua WCU.
Basta dizer qual é a sua meta de uso da capacidade,
e o DynamoDB a dimensionará para você.
Agora, caso você ultrapasse a RCU e a WCU porque está consumindo
ou escrevendo mais do que o provisionado,
não há problema algum,
pois você pode usar, temporariamente, o que é chamado de capacidade
de explosão.
Mas se você esgotar a capacidade de burst
porque ela foi totalmente consumida,
receberá uma exceção chamada
ProvisionedThroughputExceededException, que é muito
óbvia quanto ao seu significado.
Então, caso isso aconteça, você precisa
obviamente tentar novamente.
E a estratégia para repetir a gravação ou a leitura
é chamada de estratégia de repetição de backoff exponencial.
Agora vamos analisar a WCU em detalhes.
Portanto, o exame pedirá que você faça alguns cálculos
e, por isso, você precisa entender as
fórmulas para calcular a WCU e a RCU.
Portanto, uma unidade de capacidade de gravação,
WCU, representará uma gravação por segundo
para um item de até 1 kilobyte de tamanho.
E se o seu item for obviamente maior que
1 kilobyte, você consumirá mais WCUs.
Então, vamos ver exemplos para entender o cálculo.
E você pode pausar o vídeo
se quiser fazer o cálculo por conta própria.
Portanto, se você escreve 10 itens por
segundo e o tamanho do item é, em média, de 2 kilobytes,
de quantas WCUs você precisa?
Bem, vamos fazer as contas. Precisamos de 10 W, 10 itens por
segundo, ou seja, 10 vezes, e o tamanho do item é de 2 kilobytes,
que dividimos por 1 kilobyte, que
é o número de WCUs necessárias para 1 kilobyte.
E você obtém um resultado de 20 WCUs.
Portanto, esse foi um exemplo muito fácil.
Agora, no Exemplo 2, escrevemos 6 itens por segundo e,
desta vez, o tamanho do item é 4. 5 kilobytes.
Portanto, esse é um pouco mais complicado.
Portanto, precisamos de 6 vezes 5 dividido por 1, que é 30 RCU. Por quê?
Bem, porque o 4. 5 kilobytes sempre
serão arredondados para o kilobyte superior
pelo DynamoDB para se ter uma ideia de quantos WCUs você consumiu.
Portanto, lembre-se de que você precisa
arredondar para o quilobyte superior para as WCUs.
Agora, se você escrever 120 itens por minuto e o tamanho
do item for de 2 kilobytes, o truque aqui
é que temos itens por minuto.
Portanto, você precisa fazer
um pequeno cálculo, que é 120 dividido por 60 para obter itens por segundo.
E isso nos dá 4 WCUs.
Certo, então as unidades de capacidade de gravação são muito
básicas e, honestamente, muito fáceis de entender.
Os mais complicados ficarão em torno da leitura.
Portanto, primeiro precisamos
definir dois tipos de modos de leitura para o DynamoDB, que
são a leitura fortemente consistente
e a leitura eventualmente consistente.
Portanto, se você considerar o DynamoDB,
ele é um banco de dados sem servidor, é
claro, mas, nos bastidores, há servidores.
Você simplesmente não os vê nem os gerencia.
Portanto, temos servidores,
e vamos considerar apenas três servidores neste
momento para simplificar bastante,
mas é óbvio que há muito mais.
E seus dados serão distribuídos
e replicados em todos esses servidores.
Agora, se você considerar o seu
aplicativo, ele fará gravações
em um desses servidores.
E, internamente, o DynamoDB replicará esses direitos
em diferentes servidores, como o Servidor 2 e o Servidor 3.
Agora, quando seu aplicativo lê do DynamoDB,
há uma chance de que você não
leia do Servidor 1, mas do Servidor 2.
Agora, duas coisas podem acontecer, certo?
Se estivermos em uma leitura eventualmente
consistente, que é o modo padrão,
se fizermos uma leitura logo após uma gravação,
é possível que obtenhamos dados obsoletos porque
a replicação ainda não aconteceu se formos muito,
muito rápidos.
Mas depois de, digamos, 100 milissegundos, você
está pronto para ir, obviamente.
Mas se você fizer uma leitura fortemente consistente,
estará dizendo: "Quero ler os dados logo após a gravação".
E você obterá, com certeza, os
dados corretos que acabaram de ser escritos.
Para isso, precisamos definir
um parâmetro chamado ConsistentRead em nossa API como True.
E pode ser aplicado a GetItem,
BatchGetItem, Query e Scan.
E por que não faríamos isso o tempo todo?
Por que não gostaríamos de ter
leituras consistentes o tempo todo?
Bem, ele vai consumir o dobro da RCU.
Portanto, será uma consulta mais cara
e também poderá ter uma latência um pouco maior.
Portanto, você precisa se perguntar:
preciso de leituras eventualmente
consistentes ou de leituras fortemente consistentes?
Agora vamos falar sobre a RCU em relação a esses dois aspectos.
Uma unidade de capacidade de leitura, RCU,
representa uma leitura fortemente consistente por segundo ou duas leituras
eventualmente consistentes por segundo para
um item de até 4 kilobytes de tamanho, o que torna os cálculos um
pouco mais complicados.
E se seus itens forem maiores que 4 kilobytes, mais
RCUs serão consumidas e, novamente,
serão arredondadas para os 4 kilobytes
superiores mais próximos.
Então, vamos examinar os exemplos novamente
e fique à vontade para pausar o vídeo.
Portanto, se você tiver 10 leituras altamente consistentes por segundo
e o tamanho do item for de 4 kilobytes, de quantas
RCUs você precisa?
Precisaremos de 10 vezes 4 kilobytes dividido
por 4, o que equivale a 10 RCUs, certo?
Agora, se você tiver 16 leituras eventualmente consistentes
por segundo e o tamanho do item
for de 12 kilobytes, o que é um pouco
mais complicado, obteremos 16 dividido por 2 vezes 12 dividido por
4, o que equivale a 24 RCUs.
Portanto, neste exemplo, obviamente,
precisamos dividir 16 por 2 porque não precisamos,
porque temos duas leituras eventualmente
consistentes por segundo em uma RCU, e depois dividimos
12 por 4, o que nos dá 24 RCUs.
E o último exemplo, que
é de 10 leituras altamente consistentes por segundo
com um tamanho de item de 6 kilobytes, ok, este
é um pouco mais complicado, então o que é?
Bem, é 10 vezes 8 dividido por 4. E por que 8?
Bem. arredondamos 6 kilobytes para os 4 kilobytes
mais próximos, portanto, serão 8 kilobytes,
e você deve sempre aumentar, certo?
E, nesse caso, obtemos 10 vezes 8 dividido
por 4, que é 2, portanto, 20 RCUs.
Agora que já sabemos sobre WCUs e RCUs,
vamos falar sobre como o DynamoDB
funciona no backend com partições.
Portanto, o DynamoDB é feito de tabelas, e
cada tabela tem partições.
E as partições são apenas cópias de seus
dados que ficam em servidores específicos.
Agora, quando seu aplicativo gravar no DynamoDB, o que acontecerá
é que ele enviará uma chave de
partição, talvez uma chave de classificação e alguns
atributos.
E todos esses dados passarão
por um algoritmo de hash.
Portanto, somente a chave de
partição realmente passará por um algoritmo
de hashing para entender para qual partição deve ir.
Portanto, se pegarmos a chave de partição ID_13, ela passará
por essa função hash interna do DynamoDB.
E ele dirá, ei, sempre que eu vir ID_13,
ele irá para a Partição 1.
E se você tiver o ID_45 na segunda linha, o ID_45
passará pela função de hash, e a função de hash
dirá que esse ID_45
deve ir para a Partição 2.
E é assim que seus dados são distribuídos.
Portanto, obviamente, se você tiver o que chamamos de partição
ativa, os dados sempre serão uma tecla ativa.
Os dados sempre estarão na mesma partição.
Portanto, para calcular o número de partições,
há algumas fórmulas intensas que
você não precisa saber para o exame.
Então, vamos examiná-los rapidamente.
Mas você calcula o número de
partições dividindo as RCUs por 3.000 e as WCUs por
1.000 e somando-as.
Você também pode dar uma olhada na quantidade de dados que possui,
ou seja, o tamanho total do conjunto de dados dividido por 10 gigabytes.
E o número de partições
será o máximo dessas duas coisas.
Agora, você não precisa conhecer essa fórmula,
portanto, não se preocupe com isso, ok?
No entanto, o que você
precisa entender é que, se tiver 10 partições e fornecer
10 WCUs e 10 RCUs, elas serão distribuídas igualmente
entre as partições.
Isso significa que
cada partição receberá uma WCU e uma RCU.
E esse é o ponto que quero que você se lembre, certo?
As WCUs e RCUs serão divididas e distribuídas
igualmente entre as partições, o que nos
leva à limitação.
Portanto, caso você exceda as RCUs ou WCUs, e isso está no nível da partição,
você receberá uma ProvisionedThroughputExceededException.
Talvez porque você tenha uma tecla de atalho,
ou seja, uma tecla de partição está sendo lida muitas
vezes de uma partição específica, talvez porque
você tenha um item popular, partições de atalho
ou itens muito grandes, porque, obviamente, quando
a WCU e a RCU são computadas, isso depende do tamanho do item.
Portanto, se você ler ou escrever um
item muito grande, consumirá muitas RCUs ou WCUs.
Agora, as soluções para atacar essa ProvisionedThroughputExceededException
são, em primeiro lugar, fazer um backoff exponencial
quando a exceção for encontrada, o que, se você estiver usando o SDK, é algo que já está incluído.
Você precisa distribuir as chaves de partição
o máximo possível, que
foi o exercício que fizemos na primeira aula para entender
como podemos escolher uma chave de partição realmente boa.
E se esse for um problema de RCU,
porque você está lendo um ponto de dados e uma
partição muito, muito intensamente,
então daremos uma olhada no recurso
chamado DynamoDB Accelerator, ou DAX.
Agora, o último modo que precisamos entender,
e esse é um modo muito mais fácil de entender, é o
modo de capacidade de leitura/gravação sob demanda, que aceitará
automaticamente todas as leituras e gravações e será dimensionado para cima e para
baixo com base em sua carga de trabalho.
Portanto, não há necessidade de planejamento de capacidade.
Você não especifica a RCU ou a WCU.
É ilimitado. Não há limitação.
Mas, obviamente, isso é mais caro.
E você cobrará pelas leituras e gravações reais.
Essa é chamada de unidades de solicitação de leitura,
ou RRUs, e unidades de solicitação de gravação, ou WRUs.
Os cálculos são os mesmos, mas a ideia é que, como temos
todas as solicitações bem-sucedidas, não se trata de uma
capacidade da qual falamos.
Está apenas na solicitação.
Para que você tenha uma visão geral,
o on-demand é cerca de 2. Cinco vezes mais caro do que a
capacidade provisionada.
Portanto, certifique-se de que ele
seja usado somente para tipos específicos de
casos de uso, por exemplo, cargas de trabalho
desconhecidas ou quando o tráfego de aplicativos for imprevisível.
Então é isso para os modos de capacidade no DynamoDB.
Espero que tenham gostado e nos veremos na próxima palestra.
