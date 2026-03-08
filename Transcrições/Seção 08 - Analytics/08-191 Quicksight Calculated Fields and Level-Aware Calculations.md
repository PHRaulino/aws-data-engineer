os campos calculados no Quicksight estão aparecendo
no exame agora, então vamos nos aprofundar um pouco mais nisso.
Portanto, os campos calculados são exatamente o que parecem ser.
Ele permite que você crie novos campos com base em outros campos
do seu conjunto de dados que está no
SPICE e, com sorte, por estar no SPICE, isso
pode ser computado com bastante rapidez.
Assim, por exemplo, se você
quisesse computar coisas como margem de
lucro, poderia fazer algo assim.
É muito simples quando você está
no Quicksight.
Há apenas um pequeno botão para Add Calculated
Field (Adicionar campo calculado) e você pode digitar
a expressão que quiser, e os operadores
disponíveis são os suspeitos de sempre.
Você pode dividir e multiplicar
ou usar operadores lógicos como e, ou, não, ou adicionar
e subtrair, tudo, tudo o que você espera.
Você também pode usar funções condicionais.
Assim, você pode usar a lógica condicional, como if ou else
ou not e coisas do gênero.
Assim, você pode configurar casos mais complicados em que
um determinado campo só entra em ação em determinadas condições,
o que é interessante.
Você também pode ter funções de data.
Portanto, se você quiser calcular uma data que
seja seis meses a partir desta data ou algo parecido,
ou apenas formatá-la de uma maneira diferente, isso também
estará disponível por meio de campos calculados
e funções numéricas e matemáticas, portanto, não apenas
operadores.
Você também pode aplicar funções como logaritmos, raízes quadradas,
arredondamento, teto, o que quer que seja, e aplicar
isso aos seus dados também.
Se você tiver dados de cadeia de caracteres,
poderá executar as funções usuais de
cadeia de caracteres esperadas, concatenação,
alteração da capitalização, o que quer que seja.
Há também várias funções de cálculo de tabela, como
uma média ou o mínimo ou o máximo
em execução à medida que você percorre o conjunto
de dados.
Portanto, eles também estão disponíveis por meio de campos calculados.
E também temos funções de agregação
sobre as quais falaremos mais detalhadamente,
como média, mínimo, máximo ou desvio
padrão em todo o conjunto de dados.
Você também pode fazer isso em um campo calculado.
Por falar em agregações, há algumas maneiras de fazer isso
por meio de cálculos com reconhecimento de nível,
ou LAC, para abreviar.
E você tem, isso é algo que você precisa saber.
Portanto, isso permite que você controle a granularidade
desses cálculos.
Portanto, quando estamos fazendo agregações do nível de
exibição, normalmente as colunas que você vê em um determinado conjunto
de dados são o que você vai somar em um determinado
campo agregado.
Então, dê uma olhada neste exemplo
à direita, que é algo chamado de LAC-A ou funções agregadas LAC.
E, neste estudo de caso,
a coluna de soma de vendas fornecerá o total
de vendas para a combinação de todos os
outros campos que você vê.
Portanto, para uma determinada
combinação de região, país e produto, a soma
da coluna de vendas será a venda específica
para essa região, país e produto.
Mas você pode mudar isso
e também fazer algo em um nível diferente.
É por isso que eles o chamam de cálculos com reconhecimento de nível.
Portanto, podemos dar um passo adiante
e dizer que, neste exemplo,
também queremos exibir o total de vendas de todo
o país, e não apenas a combinação
de país, região e produto nesse
caso, certo?
Portanto, se você observar
isso, verá que todas as linhas da Argentina
têm o mesmo valor, pois
essa é a soma das vendas de todo o país.
E se você somar
todos esses valores individuais
de vendas, isso deve chegar a 35.764 e 31 centavos.
Portanto, a sintaxe ali, você pode
dizer soma ou qualquer outra função agregada,
você também pode fazer o percentil do contador, coisas assim.
Entre parênteses, você
começaria com a coluna que deseja agregar,
neste caso, vendas, e, em seguida,
entre colchetes, a combinação de campos que deseja
agregar.
Portanto, nesse caso, não estou agregando
por região, país e
produto, estou agregando apenas por país, certo?
Portanto, e a propósito, isso nem precisa
estar no visual.
Portanto, eu poderia estar agregando em algum
campo que nem sequer está nesse relatório.
Não precisa estar lá dentro.
Isso é aplicado antes do nível de exibição.
Portanto, antes de calcular o resultado
real desse relatório, você pode aplicar essa
agregação antes de chegar a esse nível
e calcular o que quiser em um
nível diferente.
Essa é a ideia aqui.
E também temos o LAC-W, janela de
cálculos com reconhecimento de nível,
que é um pouco mais difícil
de entender.
Janela, geralmente pensamos nisso no
contexto de uma janela deslizante de
tempo, mas não é isso que queremos dizer aqui.
Estamos agregando sobre uma janela ou partição aqui,
onde estamos calculando algum agregado sobre alguma
janela, algum subconjunto dos dados aqui, e
não é necessariamente o tempo, e podemos
adicionar isso a cada linha.
Portanto, serão agregações baseadas em
funções de janela como sumover ou maxover ou denseRank.
Neste exemplo, vamos mostrar
um relatório de itens de linha individuais
em pedidos, certo?
Portanto, temos faturas que têm um ID de pedido.
Cada fatura pode ter várias linhas para
produtos individuais, certo?
Portanto, se usarmos a agregação padrão aqui,
ela me dará apenas a soma das vendas para esse item de linha.
Nesse caso, apenas
o valor de venda desse único item de linha, certo?
Mas se também quisermos exibir o valor
do pedido em todos os produtos desse pedido, poderemos fazer
isso com o LAC-W.
Portanto, nesse caso, estamos dizendo para somar a coluna de vendas,
por ID do pedido.
Então, para todo o ID do pedido, quero
todas as vendas dentro desse ID do pedido.
E então temos outro parâmetro,
PRE_AGG ou PRE_FILTER.
PRE_AGG significa que aplicaremos
essa janela antes de qualquer agregação em nível de exibição.
Portanto, nesse caso, a agregação em nível de exibição seria
a combinação de todos esses campos diferentes.
Vamos dar um passo adiante em relação a isso.
Portanto, estamos dizendo que, em todo o ID
do pedido, quero agregar em todo o pedido.
O PRE_FILTER também é uma opção.
E isso aplicará seu cálculo antes
de qualquer filtro de nível de exibição também.
Portanto, se você tivesse um filtro
aplicado aos seus dados, como mostrar apenas as vendas
que são maiores do que algum
valor ou algo do gênero,
você poderia contornar isso também usando o PRE_FILTER.
E algumas aplicações disso, por exemplo, se eu tiver
esse campo calculado do valor
total do pedido, poderei
fazer coisas como criar um histograma da frequência
com que esse valor do pedido aparece para
um determinado item, certo?
Portanto, um exemplo melhor seria usar a contagem e o número
total de contagens de algo em algum contexto
e fazer um histograma disso.
Portanto, se você precisar criar uma visualização de histograma
ou algo do gênero em
um nível de agregação diferente do relatório
real, poderá fazer isso com a janela
de cálculos com reconhecimento de nível, LAC-W.
Mais uma observação sobre agregações
e, bem, campos calculados em geral: há um problema de precisão.
Muitas vezes, você usará um tipo de campo FIXED para dados
decimais.
Portanto, se você tiver dinheiro ou algo do
gênero, provavelmente verá muitos tipos de dados FIXOS.
E o problema com o FIXED é que ele só lida
com até quatro pontos decimais de precisão.
E isso pode ser um problema quando se está fazendo cálculos.
Portanto, se eu estiver dividindo valores juntos, quatro casas
decimais podem não ser suficientes, certo?
Portanto, um dividido por três, por exemplo,
é 0. 3333333 para sempre, certo?
Quatro casas decimais não são suficientes, necessariamente.
Isso pode ser um problema.
Isso também pode ser um problema de arredondamento.
Portanto, se eu tiver dados mais
precisos que estão sendo importados para o meu conjunto de
dados, arredondá-los e cortá-los em quatro casas
decimais também pode ser um problema
e pode resultar em problemas de estouro.
Então, o que você faz em relação a isso?
Bem, há alguns anos, não muito tempo atrás, eles introduziram
o tipo de dados FLOAT no Quicksight em SPICE, e isso oferece
mais precisão.
Portanto, é exatamente o que
parece, um tipo de dados de ponto flutuante que pode ter
precisão de até 16 dígitos significativos.
E se você contar isso, você sabe, temos um, você sabe, antes
do ponto decimal e todo o resto
depois, são 15 pontos
decimais, basicamente.
Isso pode ajudá-lo a evitar erros de arredondamento nas importações
de dados e também a evitar erros de precisão quando estiver
fazendo cálculos que possam envolver
divisão e coisas do gênero.
Portanto, se você vir uma pergunta sobre precisão de dados,
lembre-se de que o FIXED o limitará
a quatro pontos decimais de precisão.
E se você estiver fazendo cálculos com base nisso,
isso pode causar problemas.
Portanto, quatro casas decimais podem não ser suficientes.
Nesse caso, usar um tipo de dados FLOAT pode ser a resposta.
