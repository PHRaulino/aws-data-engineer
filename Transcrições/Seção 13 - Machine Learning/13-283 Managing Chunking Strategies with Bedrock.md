suas opções para a fragmentação em
Bedrock? Posso realmente controlar como as
informações são armazenadas em uma base
de conhecimento e a granularidade dessas
informações? Bem, você tem algumas opções.
Portanto, o Standard Chunking é uma
espécie de abordagem mais direta, que
não tem nada de sofisticado.
Eles se baseiam apenas em heurística.
Portanto, uma abordagem é um tamanho fixo.
Assim, posso dizer: "Quero um determinado
número de tokens
por bloco". E, por tokens, essas são as
coisas
subjacentes às quais os grandes modelos de
linguagem
codificam as palavras, portanto, não é
necessariamente verdade
que um token equivale a uma palavra, mas,
às vezes, esse é o caso, certo? Então,
você pode pensar em tokens como palavras
aqui.
Então, você dirá: "Quantos tokens tenho em
um
bloco e também qual é a porcentagem
de sobreposição que tenho?" Agora, a ideia
da sobreposição é garantir que eu tenha
um pouco mais de contexto dos blocos
que precedem e seguem esse bloco, certo?
Dessa forma, posso ter certeza de que
não estou perdendo alguns desses dados
contextuais.
Então, como um exemplo muito simples aqui
à
direita, digamos que eu esteja dividindo o
texto
"Space, the final frontier" (Espaço, a
fronteira final).
Essas são as viagens da nave estelar
Enterprise.
Se eu quiser um tamanho de bloco
de 5 e uma sobreposição de 20%,
20% de cinco é um token, certo?
Portanto, terei cinco tokens por bloco e,
para simplificar, assumirei que um bloco
equivale
a uma palavra e uma sobreposição
de um bloco em cada lado.
Portanto, vou começar pelo início
Espaço, a fronteira final, Estes.
Esses são os primeiros cinco trechos do
texto.
A próxima parte será: These are the
voyages of.
Devido a essa sobreposição, estou
repetindo esse token.
E, mais uma vez, da Starship Enterprise,
repetindo a sobreposição da palavra of do
bloco anterior, de modo que é assim
que funciona o chunking de tamanho fixo.
Na prática, você provavelmente teria
tamanhos de
pedaços muito maiores porque esses trechos
individuais
não serão semanticamente significativos
por si só.
Agora, a configuração padrão é de 300
tokens por bloco e,
ao mesmo tempo, ela também respeita os
limites das frases.
Portanto, se for necessário aumentar um
pouco
mais para preservar uma frase completa
em um bloco, ele o fará.
Portanto, normalmente, você não quer
quebrar as
frases se não for necessário, porque uma
frase, em seu significado, é uma espécie
de pensamento coerente de algum tipo.
Acabar com isso seria ruim.
Portanto, a estratégia padrão de
fragmentação, a
estratégia padrão de fragmentação é 300
por
bloco, e não vou dividir frases nos
limites desses blocos se eu puder evitar.
Então, esse é um bom ponto de partida,
certo? 300 tokens, 300 palavras, capturam
algumas
ideias bastante complexas, mas estamos nos
certificando
de não torná-las muito grandes e também
de não cortar as frases no meio.
Você também pode optar por não ter nenhuma
fragmentação
e fazer com que cada documento alimentado
na Base
de Conhecimento da Bedrock seja sua
própria fragmentação.
E isso lhe dá mais controle no estado de
pré-processamento,
portanto, se você quiser pré-processar
seus próprios dados da forma
que quiser para dividi-los da maneira que
desejar, se
você gerar cada parte em seu próprio
documento e
depois disser: "Ei, Bedrock, aqui está uma
pilha de
documentos para colocar na minha Base de
Conhecimento sem
dividir em partes", então ele fará o que
você
lhe der, e cada documento será sua própria
parte.
Portanto, é nesse momento que você pode
usar
a opção sem fragmentação se já tiver
fragmentado seus dados antecipadamente em
documentos individuais.
Agora, se você quiser ficar mais
sofisticado,
podemos fazer o Hierarchical Chunking,
certo?
Então, esses são basicamente blocos
pai/filho
aninhados, nos quais temos blocos maiores
que se dividem em blocos menores.
E a ideia aqui é que a busca inicial
atinja esses pedaços filhos, certo? E isso
nos dará
um pouco mais de precisão, certo?
Portanto, estaremos
atingindo aquela parte muito específica do
texto que
é relevante, esperamos, para o assunto da
consulta.
E, para obter mais contexto, subiremos na
árvore
e obteremos cada vez mais contexto a
partir
desses pedaços maiores de dados, certo?
Portanto, a
ideia aqui é obter melhor precisão em
sua recuperação a partir desses embeddings
menores.
Portanto, embeddings menores significam
mais precisão, mas
estaremos abrindo mão da abrangência, do
contexto que envolve esses pequenos
trechos.
Portanto, para recuperar isso, iremos a
esses pais na hierarquia para obter
o contexto mais amplo do que
se trata esse pequeno trecho, o
que é uma ideia interessante.
À direita, você pode ver isso mais ou
menos explicitado aqui.
Estamos apenas quebrando um pouco
o lado esquerdo dessa árvore.
Portanto, neste exemplo específico, temos
um tamanho
de bloco pai de 6, que
é uma espécie de segundo nível.
Estamos começando com o mesmo pedaço maior
de texto, que será dividido em seis
pedaços, e temos um tamanho de pedaço
filho de 3 com uma sobreposição de
1, e é isso que acaba aparecendo.
Portanto, no nível filho inferior, temos
o Space, o final com o
tamanho de 3 do bloco filho.
Temos uma sobreposição de 1, portanto, o
próximo bloco
será a fronteira final, Esses, e assim por
diante,
certo? Portanto, se obtivermos um
resultado em uma dessas
notas filhas, poderemos subir um nível até
o
tamanho de 6 do bloco pai e obter
um pouco mais de contexto dessa forma,
certo?
E você pode expandir isso para os outros
blocos e blocos pai e filho mostrados
aqui.
Ilustrei aqui apenas o lado esquerdo da
árvore, mas você entendeu a ideia.
Além disso, falamos sobre o Semantic
Chunking
um pouco antes, usando um modelo
de base para fazer os pedaços.
Assim, posso dizer: "Ei, modelo de
fundação, descubra
a melhor maneira de dividir essas
informações e
tente descobrir como preservar as ideias
em um
determinado corpus de dados em vez de ter
apenas um tamanho fixo de bloco".
Portanto, ao
fazer isso, você especificará o número
máximo de
tokens que deseja que esses blocos tenham
e,
ao mesmo tempo, respeitará os limites das
frases, de modo que possa dizer: "Ei,
modelo de fragmentação semântica, divida
isso, mas
certifique-se de que os blocos não sejam
maiores que três kilobytes ou o que
quer que seja". Você também pode
especificar
um tamanho de buffer, que é basicamente
o número de frases adjacentes por frase
que você considera ao fazer essas
incorporações.
Assim, por exemplo, se eu tiver um tamanho
de buffer de um, isso significa que, para
cada frase que esse modelo estiver
analisando para
a fragmentação semântica, ele também
analisará a
frase de cada lado, totalizando três
frases.
Agora, se você definir esse tamanho
de buffer muito grande, introduzirá muito
ruído, certo? Portanto, você receberá
muitas
informações irrelevantes, mas se for muito
pequeno, poderá perder um contexto
importante.
Portanto, um tamanho de buffer muito
grande introduz ruído,
um tamanho de buffer muito pequeno
significa que você
perde um contexto importante, mas pode ter
mais precisão.
Esse parece ser o tipo de coisa que
o exame pode querer testar em você.
Não sei, na verdade, ainda não o fiz
até o momento desta gravação, mas esse é
o tipo de coisa que você precisa saber.
Além disso, há um limite de percentil de
ponto de interrupção que você pode
especificar e
que especifica o grau de semelhança
semântica que
um bloco deve ter com ele mesmo.
Portanto, se você tiver um limite de
percentil
de ponto de interrupção mais alto, isso
resultará
em mais pedaços distinguíveis, mas haverá
menos pedaços
e eles serão maiores, certo? Portanto, é
isso
que você precisa saber sobre esse
parâmetro específico.
Um pequeno exemplo disso aqui ao lado,
bem,
não é bem um exemplo porque, francamente,
esse
pequeno trecho é uma espécie de pensamento
próprio.
Portanto, na prática, a fragmentação
semântica provavelmente
não dividiria isso de forma alguma.
Obviamente, isso custa dinheiro.
Na verdade, estamos usando um
modelo de fundação potencialmente caro
para fragmentar grandes quantidades de
dados, e isso aumenta.
Você será cobrado pelo custo do
modelo de fundação subjacente para fazer
isso, portanto, use-o com sabedoria.
