geral e como ele é útil para a
pesquisa,
mas como ele é especificamente útil para
uma IA
generativa? Bem, como vimos anteriormente,
o Bedrock Vector
Stores tem uma opção proeminente para usar
o
OpenSearch como seu armazenamento de
vetores e agora
também tem um recurso de armazenamento de
vetores.
E, além disso, também pode ser sem
servidor.
Observe que serverless não é a
mesma coisa que scale to zero.
Como você pode aprender da maneira mais
difícil, se
você deixar um armazenamento de vetores
sem servidor em
funcionamento, ainda receberá uma cobrança
de algumas centenas de
dólares por mês, mesmo que não o esteja
usando.
Portanto, esteja ciente disso.
Acho que isso não vai estar no exame, mas
só estou lhe dizendo isso para sua própria
segurança.
No entanto, o exame, em sua forma
atual, pelo menos trata o OpenSearch como
o tipo de implementação principal para
apoiar uma base de conhecimento Bedrock.
Pessoalmente, acho que isso pode ser
incluído
no novo recurso de vetores S3.
Na verdade, há uma maneira muito mais
fácil e
simples de fazer isso agora usando o S3,
em
que você pode simplesmente jogar dados no
S3
e dizer: "Ei, S3, faça vetores com isso".
E então posso vincular isso à minha base
de conhecimento.
Gosto um pouco mais dessa opção, mas acho
que
ela é um pouco nova demais para este
exame.
Mas, para que você tenha uma ideia,
os vetores S3 também estão na moda.
Agora, os armazenamentos vetoriais no
OpenSearch não
estão limitados às Bases de Conhecimento
Bedrock.
Se você configurar um armazenamento de
vetores no
OpenSearch, poderá usá-lo também em outros
sistemas.
É claro que, se você tiver um
sistema no SageMaker AI, algo construído
com
base em um modelo HuggingFace ou em
seus próprios modelos personalizados para
geração aumentada
de recuperação, também poderá integrá-los
a eles.
Portanto, não se trata apenas de Bedrock.
Agora, outra coisa que pode estar no exame
é a pesquisa semântica versus a pesquisa
híbrida.
Portanto, a semântica é mais ou menos o
que fazemos
por padrão, certo? Então, dizemos: aqui
está um pedaço de
texto que eu converti em um vetor de
incorporação.
Encontre o vetor de incorporação mais
próximo que você tem
e qual parte dos dados está associada a
ele.
Portanto, essa é a pesquisa semântica.
Estamos apenas fazendo comparações de
vetores em vetores de incorporação.
No entanto, como vimos, isso apresenta
alguns
desafios para obter os dados relevantes
corretos.
Portanto, se combinarmos isso com uma
espécie de pesquisa de palavras-chave
antiga,
talvez possamos obter resultados ainda
melhores.
Portanto, uma ideia seria usar uma
abordagem híbrida em que
combinamos a pesquisa vetorial e a
pesquisa por palavra-chave.
E isso exige que você
precise indexar suas palavras-chave para
metadados, além desses vetores também.
Mas é uma técnica poderosa para
realmente melhorar a relevância de seus
resultados da loja de vetores.
Portanto, não pesquisamos apenas os
embeddings
e também pesquisamos as correspondências
reais
de palavras-chave ao mesmo tempo.
Agora, entrando nos detalhes do
OpenSearch, há três
mecanismos de alto nível que podemos usar
para a pesquisa de vetores no OpenSearch.
Eles são o Facebook AI Similarity,
abreviado FAISS,
que é o que a maioria das pessoas
usa, a biblioteca espacial não métrica,
NMSLib, e
o Apache Lucene e algumas maneiras de
usá-lo.
Como faço essa pesquisa de vetores?
Basicamente, preciso encontrar
o vetor de incorporação mais próximo de um
vetor
de incorporação que estou fornecendo, uma
maneira de fazer
isso é a pesquisa exata do vizinho mais
próximo.
Mas, como você pode imaginar, isso é muito
lento.
Isso exige que eu calcule a distância
do meu vetor a todos os outros
vetores e encontre a menor distância.
Você não quer fazer isso no mundo real.
Há uma abordagem muito mais rápida
chamada de vizinho mais próximo
aproximado,
que geralmente é boa o suficiente.
Pode não ser perfeito, mas para nossos
propósitos vale a pena a troca.
E há duas opções aqui sobre como
configurar isso.
Um algoritmo para ANN é o hierarchical
navigable
small world (mundo pequeno navegável
hierárquico) ou HNSW.
E ainda há o arquivo invertido ou FIV.
Portanto, a diferença aqui que você deve
lembrar é
que o HNSW é rápido, mas usa muita RAM.
Portanto, se você tiver um conjunto de
dados muito
grande, talvez ele não seja tão bem
dimensionado.
Se você tiver uma tonelada de dados para
um conjunto
de dados realmente grande, o IVF poderá
ser uma
opção melhor, mas você estará trocando o
desempenho de
recall por essa velocidade extra e
desempenho de memória.
Portanto, se você tiver um conjunto de
dados enorme e a
RAM for um problema, o IVF é a sua opção.
Caso contrário, se você valoriza a
velocidade
e a eficiência acima de tudo,
a HNSW é a opção ideal.
Você também pode ajustar o HNSW ainda
mais.
Há muitos parâmetros, mas estes são
os três que você deve conhecer.
Uma delas é M, que
é a quantidade de bordas
por nó usadas pelo algoritmo.
E você precisa saber que um M mais
alto resulta em mais uso de memória.
Portanto, o resultado é um gráfico mais
denso e
uma melhor memorização, mas à custa de
mais memória.
Há ainda o ef_construction, que é
o tamanho da lista dinâmica usada
para o gráfico KNN internamente.
KNN é K Nearest Neighbors, um
algoritmo de aprendizado de máquina.
Esse é um curso diferente, mas quanto
mais alto for o valor de
ef_construction, mais lenta será a
indexação,
mas o gráfico será mais preciso.
Depois, há o ef_search, que é o grau
de profundidade com que exploramos esse
gráfico.
Portanto, como você pode imaginar, um
valor
mais alto proporcionará valores de
recuperação mais
altos, melhor qualidade, mas diminuirá o
desempenho
da pesquisa, certo? Portanto, lembre-se de
quais são as vantagens e desvantagens
desses diferentes parâmetros para o HNSW.
E alguns outros pontos mais finos do uso
do OpenSearch como seu armazenamento de
vetores, apenas
coisas aleatórias que podem aparecer no
exame.
Existem diferentes técnicas de compactação
de vetores.
Portanto, diferentes métodos ANN têm suas
próprias técnicas
de compactação de vetores. E é bom que
você possa fazer isso e imaginar que,
normalmente,
você tem mil ou mais dimensões por vetor
e, se estiver codificando um pedaço de
texto
de 300 caracteres com mil dimensões,
estará usando
mais espaço para os embeddings e para os
dados em si, o que fica um pouco
estranho, mas existem técnicas de
compactação de
vetores que podem ajudar com isso e,
normalmente, isso é feito de forma oculta.
Portanto, você não precisa pensar muito
sobre isso,
mas há algumas técnicas que você deve
conhecer.
Um deles são os vetores binários.
Portanto, se eu converter esses valores de
dimensão de ponto
flutuante em apenas sequências de bits,
isso pode economizar muito
espaço, certo? Portanto, em comparação com
um número de
ponto flutuante de 32 bits, se eu puder
reduzi-lo
a um único bit, economizarei 32 vezes a
compactação.
Esses não serão embeddings úteis por si
só, mas
podem ser úteis para a pesquisa rápida de
distância.
Portanto, essa é uma ferramenta útil para
acelerar essas pesquisas.
Outra opção é o FP16, que ainda
oferece um vetor de incorporação útil.
Ele está apenas quantizando-o de uma
resolução de 32 bits para 16 bits.
Portanto, ainda é um valor de ponto
flutuante nesses vetores, mas com um
pouco menos de resolução e, normalmente,
não há problema, e é isso
que o HNSW faz por padrão.
Portanto, essa é a compactação de vetor
padrão do
HNSW, FP16, lembre-se disso, significa
apenas valores de ponto
flutuante de 16 bits em vez de 32 bits.
Alguns pontos mais específicos que você
talvez precise conhecer.
Como escolho uma estratégia de
fragmentação quando estou lidando com
essas coisas? Falamos sobre sharding
anteriormente, mas há algumas
considerações
específicas sobre a pesquisa semântica.
Portanto, precisamos equilibrar o tamanho
dos fragmentos e a
proporção da CPU, obviamente, como você
faz, queremos ter
certeza de que você tem potência de CPU
suficiente para o número de fragmentos que
possui.
Isso é um fato.
Mas um ponto mais delicado aqui é
que, se você estiver fazendo apenas
uma pesquisa semântica, essas são
consultas
bastante simples, certo? Portanto, não há
muita coordenação acontecendo entre os
fragmentos.
Portanto, se você estiver fazendo apenas
pesquisa
vetorial, pesquisa semântica, poderá usar
fragmentos maiores,
da ordem de 30 a 50 gigabytes.
Mas se você estiver fazendo uma busca
híbrida, em que ainda faz a busca
tradicional por palavras-chave, é melhor
usar shards
menores, pois você fará mais coordenação
entre
shards para essas consultas de
palavras-chave, certo?
Portanto, é isso que deve ser lembrado.
Agora, se você estiver usando a versão sem
servidor
do OpenSearch, tudo isso acontecerá
automaticamente nos bastidores.
Mas se você estiver provisionando seus
próprios fragmentos, é importante saber
disso.
Então, novamente, semântica, fragmentos
maiores, híbrida, fragmentos menores.
Há também técnicas para usar vários
índices que também podem ser úteis.
Então, digamos que você esteja indexando
diferentes
tipos de documentos ou documentos de
diferentes
domínios, talvez eles mereçam seus
próprios índices.
Dessa forma, você pode ajustar o
desempenho individualmente para
cada tipo de dados, para cada corpus de
dados.
E talvez você também queira diferentes
modelos de
incorporação para diferentes tipos de
dados, o que
lhe dá essa flexibilidade, se você tiver
uma
abordagem de vários índices para suas
incorporações.
Agora você precisará de algum tipo de
sistema
de roteamento de consultas para fazer
isso.
Portanto, preciso saber em qual índice
posso chegar
para um determinado tipo de dados, e uma
maneira de fazer isso são os índices
hierárquicos.
Portanto, a ideia aqui é que você tenha um
índice
de nível superior cuja única finalidade
seja direcioná-lo a um
índice de nível detalhado para um tipo
específico de documento.
Esse nível superior é realmente pequeno e
rápido, ele apenas direciona você para um
índice com dados mais detalhados por
domínio.
Portanto, novamente, é uma forma de
implementar esses vários índices
sobre os quais acabamos de falar, que
podem ser especializados
para diferentes tipos de dados ou para
diferentes domínios.
E, mais uma vez, eles podem ter seus
próprios
tamanhos de fragmentos, seus próprios
ajustes, seus próprios
modelos de incorporação, o que quer que
seja.
Agora existem outras maneiras de fazer a
mesma coisa.
Você poderia imaginar um modelo de
fundação
tomando essa decisão para você também, mas
essa é apenas uma maneira um
pouco mais simples de fazer isso.
Mais uma coisa, o plug-in neural para o
OpenSearch como
um armazenamento de vetores, talvez você
precise saber sobre isso.
Essa é apenas uma maneira de integrar seu
modelo
de incorporação diretamente ao pipeline de
ingestão do OpenSearches.
Portanto, o plug-in neural para o
OpenSearch permite que você inclua
esse modelo de incorporação como parte de
todo o pipeline.
Portanto, ele permite que você conecte
seu modelo de incorporação ao OpenSearch.
Portanto, você pode simplesmente jogar o
texto no OpenSearch, que ele descobrirá
como calcular o vetor de incorporação
apropriado e, em seguida, fará
a consulta do vetor automaticamente.
Portanto, se você quiser empacotar tudo o
que precisa no próprio OpenSearch, isso
pode
torná-lo uma alternativa ao uso de uma
Base de Conhecimento Bedrock, porque o
OpenSearch,
nesse ponto, pode simplesmente pegar o
texto
bruto, fazer a pesquisa vetorial e
fornecer o resultado mais relevante por
si só, usando o plug-in neural.
Outra coisa que o plug-in neural faz
é a integração com o Bedrock.
Portanto, ele permite que você chame o
modelo de
incorporação do Bedrock como parte do
processo de pesquisa.
Portanto, não precisa ser um modelo
bruto que você está transmitindo, ele
pode, na verdade, ser obtido do
Bedrock para incorporá-lo ao próprio
OpenSearch.
Portanto, se você quiser que essa
incorporação ocorra no
OpenSearch, é para isso que serve o
plug-in neural.
É disso que você precisa se lembrar.
