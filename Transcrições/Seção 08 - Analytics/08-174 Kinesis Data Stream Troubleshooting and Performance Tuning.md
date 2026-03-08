de quando as coisas dão errado e como corrigi-las.
Portanto, vamos falar um
pouco sobre as etapas de solução de problemas
para vários problemas de fluxo de dados do Kinesis com os quais você pode se deparar.
Vamos começar com o desempenho do lado do produtor.
Então, digamos que os direitos do meu produtor de fluxo
de dados estejam muito lentos.
Há algumas causas para isso.
Um deles pode ser o fato de você estar encontrando limites de serviço.
Talvez você queira verificar se há exceções de taxa de transferência
para ver se é isso que está acontecendo.
Se for o caso, as exceções podem indicar
qual é o problema.
Portanto, chamadas diferentes têm limites diferentes
e você pode estar excedendo esses limites.
Há também limites de nível de fragmento para leituras e direitos
que você pode estar excedendo.
Falamos sobre isso anteriormente, e
algumas operações também têm limites de nível de fluxo.
Portanto, para criar fluxos de lista
de fluxos e descrever fluxos no nível do fluxo, os limites de taxa estão
entre cinco e 20 chamadas por segundo.
Além disso, você pode estar contando os fragmentos quentes, ou seja, a distorção dos dados.
Falamos sobre isso na primeira seção.
Então, talvez seja isso que esteja acontecendo.
Talvez você precise de uma chave de partição
melhor para distribuir melhor suas colocações entre os fragmentos.
Talvez você tenha um fragmento quente que esteja deixando
as coisas mais lentas quando você está produzindo.
Se você tiver um grande produtor, pode ajudar
a aumentar o número de lotes.
Portanto, você pode usar a Kinesis Producer
Library com a API put records para agrupar
vários registros e enviá-los todos juntos
de uma vez.
Isso pode ser muito mais eficiente
ou talvez agregar seus registros em arquivos maiores
e, em seguida, enviar esses arquivos maiores
em vez de registros individuais.
Produtores menores gostam de um aplicativo.
O mesmo conselho se aplica aos registros de venda.
Você também pode usar algo chamado Kinesis Recorder nos
SDKs do AWS Mobile para fazer isso automaticamente.
Alguns outros problemas que você pode ver com
os produtores: se estiver
recebendo erros 500 ou 5 0 3, isso geralmente indica
que você está vendo exceções do Amazon Kinesis mais
de 1% do tempo.
A maneira de lidar com isso é implementar um mecanismo de repetição
para que você não apenas falhe, mas tente
novamente até que funcione.
Você pode estar vendo erros de conexão do Flink com o Kinesis.
Em caso afirmativo, isso pode indicar um problema
de rede ou a falta de recursos suficientes no ambiente do Flink,
ou também pode ser uma configuração incorreta do VPC.
Talvez você não consiga ir do Flink para o Kinesis
porque eles estão em sub-redes de VPC diferentes ou porque você
não está usando o peering de VPC.
Se você estiver vendo erros de tempo limite do Flink, as conexões do Kinesis
estão corretas, mas estão ocorrendo tempos limites.
Bem, você pode simplesmente aumentar o tempo limite com
a configuração de tempo limite da solicitação.
Você também pode definir um limite de fila mais alto
no produtor do Flink Kinesis e pode estar vendo erros
de limitação chegando.
Se for o caso, verifique se há fragmentos quentes.
Novamente, usando o monitoramento aprimorado no nível do fragmento
para ver o que está acontecendo.
Você também pode verificar seus logs em busca do que chamamos de micro picos, em que
você está vendo essas explosões repentinas de tráfego que
não consegue suportar, ou pode estar vendo métricas obscuras
que estão ultrapassando seus limites e que podem apontar
para esses tipos de micro picos.
Você também pode tentar uma estratégia de particionamento diferente, tentar
uma chave de partição aleatória ou apenas
tentar melhorar a distribuição das chaves.
Novamente, podem ser fragmentos quentes e, se você tiver dados
-: Skew acontecendo, uma chave de partição diferente é uma
maneira de tentar resolver isso.
Você também pode implementar um mecanismo de retrocesso exponencial,
portanto, se estiver atingindo os limites de
estrangulamento, poderá ter um sistema
que retroceda automaticamente no lado do produtor até
que as coisas sejam recuperadas e também poderá
fazer a limitação de taxa da velha escola.
Certifique-se de que você nunca está enviando mais do que uma determinada taxa.
Isso é mais do que você pode suportar.
Vamos analisar também o lado do consumidor
e alguns problemas que você pode ver no lado do consumidor.
Se eu estiver vendo registros sendo ignorados
com a biblioteca cliente da kin, isso pode significar que preciso
verificar se há exceções não tratadas nos registros do processo.
Se eu estiver vendo registros no mesmo processo de shard por
mais de um processador, isso pode indicar que o failover
está ocorrendo nos processadores de registros e talvez
eu precise ajustar essa falha ao longo do tempo.
Uma maneira de lidar com isso também
é tratar os métodos de desligamento que chegam com um zumbi de razão,
que é o que acontece quando você está vendo coisas sendo processadas
por mais de uma coisa.
Se minhas leituras estiverem muito lentas, posso
aumentar o número de fragmentos.
Esse é o tipo de coisa básica a se fazer.
Ou pode ser que meu número máximo de registros por chamada seja muito baixo.
Também pode ser que seu código seja muito lento.
Portanto, para ver se o seu código no lado do consumidor é o gargalo,
basta testar um processador vazio em comparação com o seu próprio e ver se
ele tem um desempenho melhor.
Get records pode estar retornando resultados vazios para você.
Do lado do consumidor, isso é totalmente normal.
Continue ligando e obtenha registros.
Há situações em que os dados simplesmente não estarão prontos
ainda, portanto, não se preocupe com isso.
Se o iterador de fragmentos estiver expirando inesperadamente,
isso pode indicar que você precisa de mais capacidade
correta na tabela de fragmentos no Dynamo DB sob o capô.
E, por fim, se o processamento de registros estiver atrasado, uma maneira de
ganhar tempo é aumentar o período
de retenção enquanto você tenta descobrir
o problema real.
Mas geralmente isso aponta para um problema
de recursos insuficientes.
Portanto, monitore isso usando a métrica get records, idade
do iterador, milissegundos e a métrica Millis
behind Latest enquanto tenta descobrir qual pode ser a limitação
de recursos.
Alguns outros problemas no lado do consumidor, talvez
sua função Lambda não esteja sendo invocada.
Isso geralmente é um problema de permissões na função de execução.
Portanto, verifique suas permissões de IAM na função Lambda para
garantir que o Kinesis possa se comunicar com ela.
Sua função também pode estar atingindo o tempo limite,
portanto, verifique o tempo máximo de execução dessa função Lambda.
Certifique-se de que ele seja grande o suficiente para lidar com o que você precisa fazer.
Você pode estar ultrapassando os limites de simultaneidade
em sua função Lambda e ficar de olho na métrica de idade do iterador
para ver se o Lambda está recebendo backup ou não.
Você também pode estar vendo exceções de taxa de transferência
provisionada de leitura excedida chegando no lado do consumidor,
o que indica que a limitação está ocorrendo.
Talvez seja necessário fragmentar novamente o fluxo em
resposta a isso ou reduzir o tamanho das solicitações de registros GET.
Essa também é uma situação em que o fan out aprimorado pode ajudar, portanto, essa
pode ser uma boa pergunta para o exame.
Estou vendo exceções de taxa de transferência de reprovisionamento excedida.
Uma das respostas pode ser
o uso de um leque aprimorado.
Você também pode usar
novas tentativas e recuo exponencial para tentar se estabelecer
em uma taxa de transferência
melhor que possa suportar mais algumas aqui.
Se estiver observando alta latência no lado do consumidor, você
poderá monitorar isso com a latência do Get Records e do Iterator
H enquanto tenta descobrir o que está
acontecendo e solucionar o problema.
Mas a primeira coisa a tentar é apenas
aumentar o número de fragmentos.
Talvez você não tenha o suficiente e também aumente o período
de retenção para garantir que os itens não sejam descartados.
Verifique a utilização da CPU e da memória.
Talvez você precise de mais memória para lidar com as coisas mais rapidamente.
Novamente, se você estiver vendo erros 500, é a mesma coisa
que no lado do produtor.
Isso indica que você está obtendo uma alta
taxa de exceção de mais de 1%.
Tudo o que você pode fazer
é garantir que tenha um mecanismo de repetição
para que, se receber uma
exceção, tente novamente em vez de receber um
500 e veja um aplicativo
KCL bloqueado ou travado no lado do consumidor.
Se for esse o caso, talvez seja necessário otimizar o método de registros
do processo e torná-lo mais rápido.
Talvez seja necessário aumentar o número máximo de concessões por
trabalhador ou ativar as leis de depuração do KCL para ver
o que está acontecendo com mais profundidade
e descobrir qual é o problema subjacente.
