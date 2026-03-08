bases de conhecimento funcionam em um alto
nível, mas este
exame espera que você saiba mais
profundamente sobre isso.
Para isso, vamos separar o R em RAG.
Então, o que esse estágio de
recuperação realmente faz? E como podemos
dividi-lo e ajustá-lo de forma mais
eficiente? Portanto, podemos dividi-lo, em
primeiro
lugar, em um estágio de pré-coleta.
Portanto, antes de fazermos qualquer coisa
com a
busca de dados, precisamos armazená-los em
nosso
armazenamento de vetores subjacente de
alguma forma.
E as escolhas que fazemos nesse
armazenamento fazem uma grande diferença.
Portanto, podemos escolher a granularidade
na
qual estamos armazenando os dados.
Então, estou armazenando frases
individuais de
informações para contexto? Estou
armazenando parágrafos?
Estou armazenando apenas comprimentos
fixos arbitrários
de texto, certo? Essas escolhas podem
fazer uma grande diferença na quantidade
de contexto que tenho em torno
das informações que estou recuperando,
na precisão dessas informações e
na relevância delas para a
consulta real que estou executando.
Portanto, as escolhas que fazemos sobre
como armazenamos esses
dados fazem uma grande diferença na
qualidade da resposta.
Além disso, a forma como extraímos esses
dados pode fazer a diferença.
E quando uma consulta chega, podemos optar
por reescrever a consulta para que ela
procure os dados com mais eficiência.
Portanto, tudo isso está acontecendo antes
mesmo de recuperarmos qualquer coisa em
tempo de execução, isso é pré-resgate.
Depois de fazer isso, podemos recuperar
os dados, e como fazemos isso,
bem, você sabe, depende do tipo
de armazenamento vetorial que estamos
usando,
o que não é muito interessante.
Mas depois de obtermos esses dados
recuperados,
esse contexto recuperado de nossa base de
conhecimento, precisamos fazer algo com
eles, certo?
Portanto, agora estamos no estágio
pós-recuperação, em
que precisamos, de alguma forma, dar
sentido às informações que coletamos,
talvez
classificá-las novamente, talvez decidir o
que
é mais relevante para a nossa
consulta, talvez aumentar ainda mais essas
informações e, finalmente, gerar nossa
resposta.
Então, vamos nos aprofundar mais nesse
estágio de pré-recuperação, certo?
Portanto, é
muito importante pensar em como armazenar
essas informações no banco de dados
vetorial subjacente ou em qualquer
banco de dados que seja.
Essa granularidade dos dados é muito
importante.
Portanto, você quer ter o suficiente para
ter
contexto sobre o que está sendo
recuperado,
mas não tanto a ponto de perder
a relevância do que está realmente
procurando.
E se for muito pequeno, isso também
é um problema, certo, porque você vai
pegar esses pequenos trechos de textos
que não têm nenhum significado real.
Portanto, é uma espécie de arte, certo?
Por
exemplo, se eu estiver criando um sistema
que
simule o Tenente Comandante Data, um
personagem de
"Jornada nas Estrelas: A Próxima Geração",
vou criar
isso com base em um banco de dados
de tudo o que ele disse nos roteiros
da série? Será que vou usar cada conjunto
de falas que ele disse e vou dividi-las
linha por linha? Vou dividi-las em frases
individuais?
Por que estou dando apenas as falas do
Data? Preciso apresentar as falas de
outras pessoas
ao redor dessas falas para dar mais
contexto? Talvez eu queira apenas resumir
essas
linhas, certo? Talvez eu não precise dos
dados brutos, e talvez eu possa usar
um LLM para esse tipo de coisa.
Portanto, há muitas opções que você pode
fazer aqui para controlar a qualidade
dos resultados obtidos com esse sistema.
Agora, o processo de dividir
essas informações é chamado de
chunking, um termo muito importante.
Portanto, tenho um enorme corpus de dados
que
preciso armazenar em um armazenamento
vetorial para
meu sistema de geração aumentada de
recuperação.
Como faço para dividir isso? Isso se chama
chunking, como eu divido esses dados em
pedaços
específicos de dados que podem ser
relevantes
para uma determinada consulta mais tarde,
certo?
Um pouco mais sobre chunking em geral.
Portanto, precisamos ter cuidado para não
alimentar o
modelo de linguagem grande, o modelo
básico, com
mais informações do que ele pode suportar.
Portanto, alguns modelos menores podem ter
limites para o número
de fichas que podem manipular de uma só
vez.
E se eu estiver devolvendo milhares
e milhares de caracteres de contexto,
talvez ele perca a linha de
raciocínio, mesmo que eu não atinja
esse limite, o excesso de informações
às vezes pode fazer com que
esses modelos saiam dos trilhos.
Então, às vezes, menos é mais, certo? Hoje
em
dia, a maioria dos modelos modernos de
linguagem de
grande porte pode lidar com milhões de
tokens.
Portanto, não é uma barreira tão difícil,
mas, novamente, há um limite para o
que eles podem processar com eficiência.
Outra técnica é a chamada
semantic chunking, uma técnica
interessante.
Portanto, a ideia aqui é que talvez eu
possa realmente
usar um LLM para fazer meu chunking e
dizer: "Aqui,
modelo de linguagem grande, aqui está um
grande pedaço de
dados que se encaixa em sua janela de
contexto grande.
Você descobre a maneira de dividi-lo em
pedaços.
Então, você descobre quais partes do texto
são
semanticamente semelhantes entre si e que
transmitem
o mesmo pensamento, se preferir", e faz
com que um modelo de linguagem grande
pense na melhor maneira de dividir isso.
Obviamente, isso é caro, dispendioso
e leva muito tempo.
Portanto, você sabe que não deve ir até lá
se não for necessário, mas essa é uma
opção.
Portanto, aqui está um exemplo de um
prompt
que você pode enviar a um LLM para
decompor o conteúdo em partes que façam
sentido.
E se você quiser ler isso, talvez
faça um pouco mais de sentido.
Isso foi extraído basicamente do artigo
original que teve essa ideia.
Portanto, você pode ter regras simples
e fixas, como cada frase, cada
parágrafo, cada determinado número de
tokens,
ou pode fazer algo mais sofisticado
e tentar dividir esses dados
semanticamente
usando outro modelo de base.
