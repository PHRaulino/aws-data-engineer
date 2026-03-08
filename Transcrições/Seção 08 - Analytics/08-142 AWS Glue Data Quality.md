Um recurso mais recente do Glue Studio é o
AWS Glue Data Quality.
Essa é basicamente uma etapa que você pode
injetar no seu trabalho de cola para
avaliar
automaticamente a qualidade dos dados que
chegam e, se eles violarem determinados
parâmetros ou regras que
você definiu, o trabalho poderá falhar
automaticamente ou apenas registrar algo
no CloudWatch para você.
Agora você pode criar essas regras
manualmente ou elas podem ser criadas
automaticamente para você.
Assim, você pode realmente saber a
qualidade dos dados de cola.
Ei, dê uma olhada nos meus dados de
origem.
Sei que esses dados são bons.
Deduzir algumas regras a partir disso.
Você sabe qual é o intervalo esperado dos
dados que estou vendo
aqui? Qual é o desvio padrão dos valores
típicos que estou
vendo? Devo ter alarmes em vigor se eu
exceder esses intervalos?
Certo.
E, depois de configurar essas regras de
qualidade de dados, você pode integrá-las
diretamente
aos seus trabalhos de cola, como pode ser
visto no diagrama à direita.
Assim como em outro estágio de
transformação, um de seus estágios poderia
ser a avaliação da qualidade dos dados
usando o glue data quality.
Agora, se você for criar essas regras
manualmente, ele usa
algo chamado Data Quality Definition
Language ou d d dl.
Veremos alguns exemplos disso no próximo
slide.
E, novamente, você pode fazer isso de
várias maneiras diferentes.
Você pode configurá-lo de modo que, se a
regra de qualidade de dados falhar, o
trabalho inteiro falhará.
No entanto, isso pode ser irritante, pois
se você tiver um
limite um pouco apertado demais, poderá
obter muitos falsos positivos.
Como alternativa, você pode simplesmente
relatar os resultados ao CloudWatch, onde
poderá interpretá-los e agir de acordo com
o que achar adequado.
Tudo bem.
Portanto, um pouco mais de profundidade na
linguagem de definição de qualidade de
dados.
Acredite ou não, o exame supostamente quer
que você entenda a sintaxe disso com
alguns detalhes.
E um pouco diferente de sua prática
habitual de não exigir que você escreva
código.
Mas vamos entrar em um pouco mais de
detalhes sobre a Dcdl.
Portanto, um documento no Dcdl consiste em
um conjunto de regras, que é apenas uma
lista de regras.
E um exemplo disso está à direita, para
que pareça um pouco mais real.
Assim, você pode ver que não é realmente
tão complicado de entender.
Assim, por exemplo, você poderia ter is
complete ou is unique neste exemplo à
direita, estamos
apenas verificando se temos pelo menos 100
linhas e se cada ID de cliente está
presente.
Não temos nenhum valor nulo, cada ID de
cliente é exclusivo, e assim por diante.
E também estamos fazendo algumas
avaliações, como garantir que
a integridade dos e-mails seja superior a
99%.
Cada idade está entre 0 e 120.
Bastante simples, certo? Portanto, há
vários tipos de
regras incorporadas, como média ou soma, e
você também pode usar expressões SQL
personalizadas.
Portanto, você pode usar o SQL no Dcdl, se
quiser.
Exclusividade.
Analisamos que detectar anomalias não
seria uma má ideia revisar a documentação
sobre
a AWS para obter uma lista completa,
apenas para ter certeza de que
você já viu todas elas, mas essas são
algumas das mais importantes.
Há também regras compostas que são
possíveis.
Não estamos vendo isso neste exemplo aqui
à direita, mas você pode usar
expressões como and ou or para combinar
regras em uma única regra.
Assim, por exemplo, se você disser que
minha chamada, um deve ser
maior que um ou minha chamada dois deve
ser maior que dois.
Isso poderia compor uma regra composta.
E um ponto importante disso é que essas
expressões compostas são avaliadas da
esquerda para a direita.
Portanto, se você tiver uma instrução and
e a primeira cláusula dessa instrução
for falsa, ela será ignorada e nem mesmo
analisará a segunda instrução and.
Certo.
Esse é um comportamento diferente do SQL,
em que ele realmente avalia tudo, não
importa o que aconteça.
E se você quiser um comportamento
semelhante ao do SQL, há um parâmetro de
opções adicional que você pode
passar quando estiver passando o dql que
especifica a regra de avaliação da regra
composta para esse comportamento.
Você também tem expressões como a que
estamos vendo aqui à direita.
Equals not equals less than greater than
whatever you want.
E você também pode ter filtros,
basicamente cláusulas where, muito
parecidas com as
do SQL, em que é possível filtrar coisas
com base em uma condição.
Você também pode definir constantes.
Portanto, se você tiver um trecho de SQL
que seja comum entre diferentes
expressões, poderá armazená-lo em uma
constante e reutilizá-lo entre outros
conjuntos de regras.
E você também pode rotular as regras.
Assim, por exemplo, se você quisesse
rotular um conjunto de regras para regras
que são aplicáveis a uma
determinada equipe, como finanças ou algo
assim, poderia facilmente dizer aplicar
todas as regras para um determinado
rótulo.
Portanto, tenho um conjunto de rótulos
associados à equipe financeira.
Só quero aplicá-las todas de uma vez.
Essa pode ser uma das utilidades do uso de
rótulos no Dcdl.
Um pequeno exemplo aqui de como ele se
parece na IU de cola.
Então, aqui eles criaram uma regra chamada
rule set one Rs1.
E você pode ver abaixo alguns exemplos da
linguagem da Dcdl para essas regras.
E isso foi criado pelas recomendações
automáticas.
Assim, você pode ver que é possível
executar a qualidade de dados de cola em
seu conjunto de dados.
E ele criará automaticamente essas regras
de dcdl para você.
E você pode ir até lá e editá-los, se
quiser.
Se você não concordar com as coisas que eu
sugeri.
Portanto, há alguns exemplos aqui.
Ele está dizendo que, uh, a contagem de
linhas deve estar entre esses valores.
Se eu estiver vendo menos do que o número
esperado de linhas, algo pode estar
errado.
Você pode testar para ter certeza de que
tem dados completos em determinadas
colunas.
Você pode testar para garantir que o
comprimento de determinadas colunas esteja
dentro de um determinado intervalo de
valores.
Lá.
Coisas desse tipo.
Certo.
Desvio padrão também.
Essa é uma pergunta interessante.
Portanto, você pode dizer que, bem, se a
data da infração ou o número
da multa estiver fora dos limites
esperados, também devemos fazer algo a
respeito.
Está bem.
E você pode ver, depois de executá-lo, à
direita, como seriam os resultados.
Portanto, neste exemplo aqui, o conjunto
de regras Rs one que criamos falhou porque
o desvio padrão na
data da infração e o valor da coluna visto
na data da infração não eram os esperados.
Novamente, esses são exemplos de onde os
limites podem ser um
pouco apertados demais e levar a um falso
positivo em potencial.
Mas talvez seja um problema real.
Talvez haja alguns dados incorretos ou
alguma discrepância que precise ser levada
em conta.
Isso atrapalharia sua análise mais tarde.
Portanto, esse é o recurso de qualidade de
dados de cola da AWS, relativamente
recente.
No entanto, deveria ser um jogo justo no
exame a partir de 2024, por exemplo.
