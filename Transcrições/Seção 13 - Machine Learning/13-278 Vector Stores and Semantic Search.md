Então, um componente
essencial do RAG é o armazenamento
de dados no qual você está armazenando as
coisas.
Portanto, mais uma vez, isso realmente
depende
de sua capacidade de recuperar resultados
relevantes
para o prompt que lhe foi fornecido.
E há mais de uma maneira de fazer isso,
certo?
Portanto, no contexto de Bedrock, chamamos
isso de armazenamento de
dados que é usado por uma base de
conhecimento.
Portanto, por algum motivo, a Bedrock não
a chama de geração aumentada de
recuperação,
embora seja isso que ela seja.
Agora, você poderia usar qualquer banco de
dados apropriado
para o tipo de dados que está recuperando,
certo?
Portanto, se você tiver dados de gráficos,
como
recomendações ou produtos ou relações
entre itens ou
algum tipo de gráfico de conhecimento, um
banco
de dados de gráficos é uma ótima opção.
E, em geral, isso produzirá resultados
muito bons, sendo o
Neo4j um exemplo de banco de dados de
gráficos.
Você também pode usar o Opensearch ou
algo parecido para a pesquisa de texto
tradicional, usando apenas o TF/IDF
antigo.
Não tem problema.
Se quiser fazer isso da maneira antiga
e pesquisar texto usando TF/IDF ou
qualquer
outro método, você pode fazer isso
da maneira que sempre fez antes.
Não tem problema.
E, de fato, há abordagens híbridas que
combinam essas técnicas de pesquisa mais
antigas
com técnicas de pesquisa semântica mais
recentes.
Mas é assim que praticamente todos os
exemplos
que você vê hoje em dia fazem, usando
um banco de dados vetorial e pesquisa
semântica.
Então, por quê? Bem, porque os bancos de
dados vetoriais utilizam a IA.
Portanto, o que estamos armazenando nesses
bancos de
dados vetoriais são embeddings que
codificam o significado
subjacente das informações que estão sendo
armazenadas.
E isso aproveita a IA.
Portanto, em teoria, isso proporciona
melhores resultados.
Agora, observe que o Elasticsearch e o
Opensearch podem
funcionar como um banco de dados vetorial,
e é
por isso que você verá com frequência o
Opensearch
sendo usado em bases de conhecimento no
Amazon Bedrock.
Portanto, antes de entendermos como
funcionam os bancos
de dados vetoriais ou os armazenamentos
vetoriais, precisamos
primeiro analisar o que são embeddings,
porque
esses são os vetores que estamos
armazenando.
E a incorporação é apenas um vetor
gigante que está associado aos seus dados.
Portanto, se você tiver algum pedaço de
texto
armazenado em um banco de dados vetorial,
estará
associando um vetor de incorporação a esse
texto,
que poderá ser usado para fazer pesquisas.
E isso pode ter dimensões muito altas.
Portanto, podemos ter um vetor
com milhares de dimensões.
Neste exemplo à direita, estamos usando
apenas duas dimensões para que você
possa entender o que está acontecendo.
Mas você pode pensar nisso como
um ponto no espaço multidimensional.
Normalmente, como eu disse, centenas ou
até
milhares de dimensões que representam, se
preferir,
o significado do texto que você
está armazenando associado a esse vetor.
Agora, eles são computados de forma que os
itens semelhantes
entre si fiquem próximos uns dos outros
dentro desse espaço.
Portanto, as coisas que são
semanticamente semelhantes estarão
próximas geometricamente
dentro desse espaço vetorial.
E é por isso que a chamamos de pesquisa
semântica.
Portanto, observando o exemplo à direita,
as palavras
"potato" (batata) e "rhubarb" (ruibarbo)
podem estar bem
próximas uma da outra nesse espaço
vetorial, onde
esses vetores para essas localizações
nesse espaço são
os vetores de que estamos falando, os
vetores
de incorporação para "potato" (batata) e
"rhubarb"
(ruibarbo). Eles estão apenas
geometricamente próximos um
do outro porque têm um significado
semelhante.
Ambos são vegetais ou algo do gênero.
Da mesma forma, podemos ter material
voltado para a
ficção científica em outra seção do nosso
espaço.
Você sabe, "The Starship Enterprise",
"Spaceballs", "The Orville",
todos eles podem estar em uma vizinhança
muito
semelhante dentro desse espaço vetorial
porque estão
falando de naves espaciais de ficção
científica,
certo? Agora, como você calcula esses
vetores
de incorporação? Bem, existem modelos de
fundação
de incorporação, como o Titan, por
exemplo,
que podem calcular esses vetores em massa.
Portanto, é relativamente barato dizer:
"Aqui
está uma pilha de textos.
Dê-me um monte de vetores de incorporação
que
eu possa usar para armazená-los em um
armazenamento
de vetores". E isso é fácil de fazer
porque, se você se lembrar de como os
transformadores funcionam, o primeiro
estágio é transformar seu...
Não é por isso que eles os chamam
de transformadores, mas estamos
transformando seu prompt em
tokens, que correspondem a vetores de
incorporação.
Portanto, a incorporação é uma espécie de
incorporação aos recursos
de todos esses grandes modelos de
linguagem desde o início.
Estamos apenas reaproveitando-os para
armazenar nossas informações em
um armazenamento vetorial para pesquisa
semântica aqui.
Então, os embeddings são vetores, certo?
Então, como
os armazenamos? Bem, nós os armazenamos em
um
banco de dados vetorial, certo? E isso
apenas
armazenará seus dados de texto originais
ou o
que quer que seja, pode ser imagens
também,
juntamente com seus vetores de
incorporação computados para
que possamos encontrar coisas
semanticamente semelhantes entre si.
E, mais uma vez, isso aproveita o
recurso de incorporação que o modelo
subjacente
já possui quando estava sendo treinado.
Portanto, normalmente, isso é algo muito
fácil de se conseguir
quando se está criando um sistema de IA
generativo.
Portanto, a recuperação quando você
estiver realmente fazendo uma
pesquisa no banco de dados de vetores
funcionará assim.
Portanto, primeiro você precisa criar um
vetor de
incorporação para o item que deseja
pesquisar.
Portanto, seja qual for o seu prompt, você
precisa convertê-lo em um vetor de
incorporação.
Em seguida, basta consultar o banco de
dados
de vetores para obter os principais itens
que
estão próximos do vetor que você está
procurando.
Você recebe de volta as N primeiras coisas
mais semelhantes, o
que é basicamente a mesma coisa que o
K-Nearest Neighbor.
E isso é o que chamamos de pesquisa
vetorial.
Agora, você pode dizer a si mesmo:
"E se eu tiver milhares ou milhões
de coisas em meu banco de dados?
Preciso realmente fazer uma busca linear
em
cada vetor e encontrar os que estão
mais próximos do que estou procurando?"
Bem,
não, há algumas otimizações que esses
bancos de dados vetoriais normalmente
empregam
para restringir as coisas a um
conjunto menor que você precisa pesquisar.
Portanto, basicamente haverá alguma
probabilidade subjacente de
estar próximo a um determinado vetor do
qual ele parte, e você não precisa
pesquisar tudo para encontrar esses
K-Nearest Neighbors.
Agora, existem muitas implementações de
bancos
de dados vetoriais no mercado.
Mais comumente, você pode forçar um banco
de
dados existente a fazer uma pesquisa
vetorial.
Portanto, muitas empresas de banco de
dados adicionaram recursos de vetor em
resposta ao aumento da IA generativa.
Portanto, o Opensearch e o Elasticsearch
são um exemplo notável.
Portanto, o Opensearch tem a capacidade de
armazenar
e pesquisar por vetores, e é para
isso que o Bedrock vai orientá-lo, pois
o Opensearch é um produto da Amazon,
certo? Portanto, ele faz um bom trabalho.
O Opensearch é uma opção perfeitamente
válida para fazer isso.
Mas você também pode obter bancos de dados
SQL para fazer isso.
Você pode fazer com que o Neptune faça
isso. Você pode usar o Redis para fazer
isso.
MongoDB, Cassandra, todos eles se
adaptaram a esse mundo de
bancos de dados vetoriais e pesquisa
semântica como uma opção.
Há também armazenamentos de dados
vetoriais criados
para fins específicos, como o Pinecone.
O Weaviate é outra alternativa comercial.
Chroma, Marqo, Vespa, Qdrant.
Normalmente, vejo o Pinecone mais nesse
contexto do que em qualquer outro.
Eles parecem estar ganhando a batalha.
Mas você pode armazenar isso em qualquer
banco de dados
que desejar e vincular o Bedrock a ele se
estiver criando uma base de conhecimento
com o Bedrock.
Vamos dar outra olhada em um exemplo
apenas
para esclarecer o que está acontecendo
aqui.
Digamos que eu tenha um sistema RAG que
contenha
todos os roteiros de "Jornada nas
Estrelas" e
eu queira perguntar a ele dados referentes
ao
Tenente Comandante Data, é claro, de
"Jornada nas
Estrelas: A Próxima Geração". "Fale-me
sobre sua filha
Lal." A primeira coisa que eu faria seria
computar um vetor de incorporação para
esse prompt.
Portanto, vou acessar meu modelo de base
que
pode fazer texto para incorporação e
dizer: "Pegue
esse prompt. Dê-me um vetor de
incorporação". E
esse pode ser um vetor com milhares de
dimensões, certo? Em seguida, consulto meu
banco de
dados vetorial de tudo o que Data já
disse em "Star Trek: The Next Generation".
E ele fará uma busca semântica lá.
E tudo isso é uma maneira elegante de
dizer: "Dê-me os principais vetores que
estão mais
próximos do meu vetor de incorporação que
estou
procurando", e esses serão os meus
principais resultados.
Isso é tudo o que há para fazer.
É apenas geometricamente dizer: "Qual é a
distância entre todos esses vetores? Dê-me
o
mais próximo da coisa que estou
procurando".
Normalmente, isso é feito usando uma
métrica
de cosseno, se você quiser ser técnico.
O que recebo de volta são os N principais
resultados que estão mais próximos desse
vetor de incorporação.
Portanto, essas podem ser linhas de
script, por
exemplo, que são relevantes para o prompt.
Portanto, as coisas que estão relacionadas
à Lal provavelmente voltarão.
Em seguida, apenas incorporei as
respostas que retornaram ao prompt.
Então, eu digo: "Você é o Comandante Data
de
'Jornada nas Estrelas'. Como Data
responderia à pergunta: 'Data,
fale-me sobre seu Lal de dados', levando
em
conta as seguintes falas relacionadas de
Data..." E
então eu listaria os cinco principais
resultados, ou
o que quer que seja, para essa pergunta.
Agora, você pode ver que há
muitas coisas que podem influenciar a
qualidade do resultado aqui, certo? Que
escolha tenho para K, quantas dessas
linhas semelhantes estou incluindo no
prompt.
Isso fará a diferença, certo? E o grau
de relevância deles fará uma grande
diferença.
A maneira como eu digo essa solicitação
fará a diferença.
Portanto, novamente, esses sistemas podem
ser bastante sensíveis na prática.
Mas, geralmente, você pega o prompt
original, faz uma consulta e recupera
os dados relevantes desse prompt e
os inclui no próprio prompt.
