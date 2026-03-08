geral de alto nível do AWS Step Functions.
Muito semelhante aos pipelines de dados e ao conceito aqui.
Basicamente, seu objetivo na vida é permitir
que você projete fluxos de trabalho em toda a AWS.
Portanto, ao criar um sistema para analisar seus
dados e pré-processá-los,
as funções de etapa podem ser
o que conecta todas essas etapas para criar um sistema maior.
Ele também permite que você visualize esses fluxos de trabalho com muita
facilidade, como veremos em breve.
Gera esses pequenos gráficos que
mostram a ordem em que as coisas são executadas.
Ele também tem um mecanismo avançado de tratamento de erros
e um mecanismo de repetição que fica fora do código que você
está executando na função de etapa do AWS.
Portanto, esse é um bom utilitário para poder gerenciar partes do seu fluxo
de trabalho que não funcionam.
Você sabe, não precisa
depender de que o código de cada etapa
seja capaz de monitorar a si mesmo.
O AWS Step Functions pode dar uma olhada de fora e lidar
com erros quando as
coisas não fazem o que deveriam fazer.
Ele também mantém um histórico de auditoria de todos os fluxos
de trabalho que foram executados.
Assim, você pode voltar e ver o que aconteceu historicamente
se precisar solucionar algum problema.
Ele permite que você espere
um período de tempo arbitrário entre as etapas.
Portanto, se você quiser apenas colocar algum
tempo entre essas etapas e sincronizar
com algum fluxo de trabalho comercial que
tenha, poderá fazer isso.
E o tempo máximo de execução de uma determinada máquina de estado, ou
seja, um determinado fluxo de trabalho, é de um ano.
Portanto, você pode definir um fluxo
de trabalho que abranja um ano inteiro, se quiser.
Não consigo imaginar uma situação em que você
precise fazer isso, mas, se for necessário,
ele pode lidar com processos e fluxos de trabalho de longa duração.
A sintaxe de como tudo isso funciona realmente não é importante.
Eles são definidos usando a linguagem Amazon
States baseada em JSON ou ASL.
O exame não espera que você seja capaz de analisar
ou escrever esse tipo de código ou que conheça ASL.
Você só precisa saber o que ele faz.
Portanto, desde que você saiba para que servem as Step Functions
e alguns exemplos de como usá-las, isso é o que
importa para o exame.
Portanto, vamos analisar alguns exemplos
de como você pode usar as funções de etapa no mundo real.
Aqui está um exemplo de como usá-lo para
treinar um modelo de aprendizado de máquina.
Assim, você pode ver que, quando começamos, geramos o conjunto de dados.
Neste exemplo, ele
está fazendo isso iniciando uma função Lambda.
Em seguida, ele treina o modelo usando o algoritmo
XG boost do SageMaker e, quando
termina, salva esse
modelo treinado do SageMaker e aplica a transformação
em lote a esse modelo a partir de algum conjunto
de dados que tínhamos.
Nesse ponto, ele está pronto.
Assim, você pode ver que automatizamos todo o processo de geração
de dados, treinamento de
um modelo de aprendizado de máquina usando esses
dados, salvando o modelo treinado
e aplicando os dados a esse modelo treinado, tudo
em um conjunto de etapas gerenciadas por meio
do Step Functions.
Também podemos usá-lo para ajustar um modelo de aprendizado de máquina.
Portanto, neste exemplo,
estamos gerando um conjunto de dados de treinamento
e, em seguida, iniciaremos
um trabalho de ajuste de hiperparâmetros no SageMaker, que simplesmente experimenta
diferentes parâmetros no modelo de aprendizado
de máquina para descobrir qual é o conjunto
certo de parâmetros para esse conjunto
de dados.
Ao terminar, ele extrai o caminho do modelo
e salva o modelo ajustado que foi estabelecido.
Extraímos o nome do modelo ajustado e, em
seguida, usamos isso para aplicar automaticamente
uma transformação de vários dados em
um formato de lote a esse modelo ajustado.
Então, novamente, apenas um exemplo
de como você pode usar as funções de etapa.
Não é importante para o exame entender como funciona
o aprendizado de máquina, mas é importante
saber que as funções de etapa podem automatizar
o processo de geração do conjunto de dados e alimentá-lo em um modelo
de aprendizado de máquina.
Você também pode usá-lo, por exemplo, para gerenciar um trabalho em lote.
Portanto, neste exemplo,
estamos enviando um trabalho em lote e, em seguida,
usaremos apenas funções de etapa para nos notificar
se ele for bem-sucedido ou não.
Muito simples.
Portanto, as funções de etapa não precisam ser complicadas.
Eles podem ser usados apenas para monitorar um único
trabalho e usar os recursos que ele tem para realmente monitorar e nos alertar
quando algo for bem-sucedido ou falhar em uma
determinada etapa.
Portanto, às vezes, as funções de etapa têm apenas uma etapa e essa é realmente toda a profundidade
de que você precisa para as funções
de etapa do AWS.
Você só precisa saber que eles gerenciam fluxos
de trabalho e fornecem uma boa representação gráfica
desses fluxos, além de
poderem monitorar se as etapas individuais
são bem-sucedidas ou não
e notificá-lo com base no que acontece.
