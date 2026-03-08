Vamos falar sobre uma
alternativa popular
ao ajuste fino, a geração aumentada
de recuperação, ou RAG, para abreviar.
E em Bedrock, chamamos isso de Base de
Conhecimento.
Portanto, a Base de Conhecimento é o que
estamos abordando aqui.
Mas para entender as bases de
conhecimento, você precisa entender o RAG.
Então, vamos falar sobre a geração
aumentada de recuperação
em um nível mais alto primeiro para
entender isso.
Você pode pensar no RAG como uma espécie
de
exame de livro aberto para modelos de
linguagem grandes.
Portanto, a ideia geral é que temos algum
banco
de dados externo que estamos consultando
para obter
as respostas, em vez de confiar no LLM.
Portanto, trata-se de uma abordagem do
tipo "enganar para
ganhar", certo? Em um nível muito alto, o
que
acontece é que você tem um prompt, neste
exemplo
à direita, o que o presidente disse em seu
discurso ontem? Bem, talvez o seu modelo
de base
subjacente não saiba a resposta para isso,
porque
foi depois do corte dos dados de
treinamento.
Mas você poderia dizer: "Ok, vou pesquisar
em meu banco de dados externo cheio
de artigos de notícias o que
o presidente disse em seu discurso
ontem?". E tentar encontrar artigos que
sejam semanticamente relevantes para essa
consulta.
Depois, talvez eu retorne ao texto do
artigo
que fala sobre o discurso do presidente
ontem e o incorpora à própria pergunta.
Portanto, isso transformaria a solicitação
em algo como:
"O que o presidente disse em seu discurso
de ontem? Considere o texto do seguinte
artigo
de notícias em sua resposta". Ontem à
noite,
o presidente disse o que quer que seja,
certo? Como você pode ver, é uma
abordagem bastante simples no final das
contas.
Estamos apenas dizendo: "Ok, vamos seguir
nosso ritmo.
Vou aumentar esse prompt com dados que
recuperei de algum banco de dados externo
e incluí-los no próprio prompt." Então,
essa
é a ideia de alto nível.
Basta trabalhar essas respostas do banco
de
dados ou, na linguagem de Bedrock, de
uma Base de Conhecimento, no próprio
prompt.
E isso é transferido para
o modelo de base subjacente.
Há também maneiras de incorporar
ferramentas e funções
para aumentar essa base de conhecimento no
sistema.
Falaremos sobre isso quando falarmos sobre
os agentes do LLM, e
essa é uma maneira um pouco mais baseada
em princípios.
Portanto, há prós e contras no
uso da geração aumentada de recuperação.
Agora, vamos começar com os prós porque,
bem,
é nisso que a Amazon quer que você
se concentre, pois eles ganham dinheiro se
você
usar IA generativa e usar esses sistemas.
É mais rápido e mais barato, pelo menos no
curto prazo, incorporar informações novas
ou exclusivas usando o
RAG em vez de fazer o ajuste fino.
Você não precisa ajustar todo o seu modelo
toda vez que obtiver novas informações.
Você pode
simplesmente expandir seu banco de dados
para consultar
esse sistema, certo? Portanto, isso é algo
muito
fácil de fazer quando novos dados chegam.
Você não precisa voltar e fazer
essa dispendiosa operação de ajuste fino.
Você pode simplesmente incorporar isso
diretamente ao banco
de dados e pronto, certo? Portanto, é uma
maneira muito boa de manter os dados
atualizados.
No entanto, isso aumenta o número
de tokens em seus prompts, certo?
Porque você está incluindo esses
dados externos em cada prompt.
E isso também pode se acumular com o
tempo.
Portanto, às vezes, é um pouco de falsa
economia.
A atualização de informações, como eu
disse, é apenas
uma questão de atualizar um banco de
dados.
Portanto, é muito simples manter seus
dados atualizados para
um sistema de IA generativo que inclui o
RAG.
Ele também pode tirar proveito do que
chamamos de pesquisa semântica.
Portanto, uma opção muito popular para o
banco de
dados em um sistema de geração aumentada
de recuperação
é algo chamado de banco de dados vetorial.
Falaremos sobre isso daqui a pouco.
Mas a ideia por trás de um banco
de dados vetorial é que ele usa
embeddings,
que codificam o significado subjacente de
uma determinada
passagem de texto ou qualquer outra coisa.
Portanto, podemos fazer uma pesquisa que
tente encontrar a
passagem de texto em nosso armazenamento
de dados que
seja semanticamente mais semelhante ao
prompt em si.
Portanto, uma forma sofisticada de
aproveitar a
IA no processo RAG na própria pesquisa
de vetores, no próprio armazenamento de
dados ou na Base de Conhecimento,
novamente, na linguagem do Amazon Bedrock.
Ele também é apresentado como uma forma de
evitar
alucinações, embora não consiga fazer isso
muito bem.
Mas isso pode evitar que o modelo
simplesmente
invente coisas no caso de você perguntar a
ele sobre algo que ele simplesmente não
sabe.
Portanto, com um modelo de fundação
existente,
se você perguntar a ele sobre algo
para o qual ele não foi treinado,
ele tem a tendência de inventar coisas.
E se você puder fornecer a ele
informações adicionais no prompt que não
sejam
inventadas, isso poderá, pelo menos,
reduzir a
quantidade de alucinações que esse modelo
produz.
E se seu chefe disser: "Ei, quero uma
pesquisa de
IA", bem, essa é uma maneira fácil de
fazer isso.
Basicamente, é isso que acontece.
É uma pesquisa alimentada por IA e
inserida
em uma IA para fornecer o resultado final.
Se você quiser ser cínico, o
que eu quero, (risos do instrutor)
você poderia dizer que o RAG
está basicamente pegando um resultado de
pesquisa e reformulando-o usando IA.
Então, no final das contas, é uma
pesquisa, certo? E
estamos apenas usando a IA para reformular
o resultado.
No entanto, isso não é totalmente verdade.
Quero dizer, o modelo de base subjacente
ainda
pode ser usado para aumentar e expandir o
que foi dado a ele no prompt.
Portanto, seu próprio treinamento ainda
entra em jogo.
Agora, e também tecnicamente, você não
está treinando um modelo com esses
dados se estiver usando o RAG.
Portanto, com um modelo de geração
aumentada de
recuperação, se você tiver algum motivo
para dizer:
"Ok, não estou realmente usando esses
dados externos
para treinar um modelo de IA porque isso
deixa algumas pessoas irritadas",
tecnicamente você estaria certo.
Você não o está treinando, não
está ajustando essas informações, não
está criando um modelo personalizado
com essas informações externas, está
apenas alimentando-as no próprio prompt.
No entanto, no lado negativo, e
isso provavelmente não estará no exame,
mas me sinto obrigado a dizer
que há desvantagens no RAG.
No final das contas, você criou o
mecanismo
de busca mais complicado do mundo, certo?
Então, como eu disse, tudo o que
o RAG realmente faz é uma busca.
E essa pesquisa não precisa ser uma
loja de vetores sofisticada com pesquisa
semântica.
Pode ser qualquer coisa.
Pode até ser uma abordagem híbrida, em que
se
usam bancos de dados tradicionais e algum
armazenamento vetorial.
Mas, no final das contas, trata-se
principalmente de um
mecanismo de busca, no qual os resultados
estão sendo
reformulados pelo modelo de base
subjacente, e essa
é uma maneira muito cara de fazer isso.
Os armazenamentos de vetores usam muitos
dados,
muito espaço de armazenamento e muita
computação.
Ele também é muito sensível ao modelo de
prompt que você usa para incorporar seus
dados.
Portanto, como dissemos, temos que incluir
de
alguma forma essas informações que
recuperamos no
próprio prompt, e a forma como você
redige isso pode gerar resultados
diferentes.
Portanto, ele pode ser muito sensível a
pequenas coisas.
Ele também é não determinístico, como,
bem,
quero dizer, você sempre pode ajustar a
temperatura para torná-lo mais
determinístico, mas
pode ser difícil testar sistemas não
determinísticos, certo? Como avaliar um
sistema
em que você não obtém a
mesma resposta para uma determinada
entrada?
Esse é um tipo de problema.
Como eu disse, ele ainda pode ter
alucinações.
Portanto, mesmo que você esteja fornecendo
mais informações, isso não
significa que ele não vá inventar coisas,
ainda assim.
Além disso, e esse é provavelmente o
maior desafio, ele é muito sensível à
relevância das informações que você
recupera.
Portanto, a forma como você escolhe
armazenar essas informações externas em
seu armazenamento de vetores ou em seu
banco de dados
externo faz uma grande diferença na
qualidade do resultado final.
E, como veremos em um exemplo prático em
breve, muitas vezes as pessoas
simplesmente pegam um
pedaço de texto e o dividem em
pedaços com um número fixo de caracteres.
E não há garantia de que
essa parte específica do personagem
tenha sequer um pensamento coerente.
Portanto, recuperar isso, não importa o
quão sofisticado
você seja, se não for relevante para o
prompt, você não obterá um bom resultado e
ele poderá ficar completamente fora dos
trilhos, certo?
Portanto, esse é o principal problema do
RAG: obter um resultado relevante para
incorporar
ao prompt com base no próprio prompt.
Isso é mais difícil do que parece.
Deixe-me dar outro exemplo de RAG, um
que aparece em um artigo acadêmico em
algum momento, é vencer no "Jeopardy!".
Então,
digamos que eu queira criar um sistema
de geração aumentada de recuperação que
possa
vencer no "Jeopardy!" com base em algum
banco de dados externo de curiosidades
que o "Jeopardy!" possa considerar úteis.
Então, digamos que eu esteja perguntando:
"Em 1986,
o México foi o primeiro país a sediar
essa competição esportiva internacional
duas vezes". O que
acontece? Então, temos um módulo retriever
aqui.
Portanto, a primeira coisa que faremos é
codificar
a consulta em uma incorporação, certo?
Portanto, no
caso de usar um armazenamento vetorial,
digamos que
o banco de dados de perguntas do
"Jeopardy!" seja esse banco de dados
vetorial.
Primeiro, precisamos consultar o banco de
dados usando esse prompt.
Portanto, fazer isso pode envolver a
incorporação
desse prompt em algo que possamos
pesquisar.
Em seguida, esse banco de dados, ou Base
de
Conhecimento, na linguagem do Amazon
Bedrock, é acessado
para obter vários documentos relevantes
para a consulta.
Então, eu poderia dizer: "Ok, aqui estão
vários
artigos que encontrei sobre o México nos
esportes
em 1986 e espero que um ou mais
deles sejam relevantes para a pergunta em
questão".
Esses documentos são então incluídos no
próprio prompt
que vai para o gerador, o modelo de
base subjacente, para produzir uma
resposta, que, neste
caso, seria: "O que é a Copa do
Mundo?" Então, novamente, tudo o que
estamos
fazendo aqui é pegar um prompt, consultar
esse prompt em alguma Base de Conhecimento
externa, pegar os resultados, os
principais documentos
que retornam desse armazenamento de dados,
dessa
Base de Conhecimento, incorporá-los ao
prompt, passar
esse prompt para o nosso modelo de
base, que é rotulado como gerador aqui,
e obter um resultado na outra extremidade.
