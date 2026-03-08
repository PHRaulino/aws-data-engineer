mais alto. Por que ele é relevante
para este
exame? Bem, ele também pode servir como um
armazenamento
de vetores, ao que parece, com uma
extensão.
Portanto, ele é chamado de extensão
pgvector. Lembre-se disso.
Portanto, o Aurora com o pgvector pode
transformar
o Aurora em seu armazenamento de vetores
para sistemas RAG ou bases de
conhecimento.
O que isso faz é criar um novo tipo de
coluna chamado vetor, entre todas as
coisas, e ele
pode calcular as distâncias de uma das
três maneiras.
Cosseno, L2 ou produto interno são as
opções para as métricas de similaridade.
Ele também pode fazer pesquisa de
similaridade
com o IVF para HNSW, ambos
discutidos anteriormente no contexto do
OpenSearch.
Portanto, se você quiser mais detalhes,
volte lá.
E também adiciona operadores vetoriais
para SQL.
Portanto, é aqui que ele acrescenta algo
novo.
Portanto, isso permite que ele faça coisas
que o OpenSearch não pode fazer.
Portanto, se você precisar fazer uma
lógica de
filtragem complexa no que está saindo do
seu
armazenamento de vetores, poderá escrever
expressões SQL que
podem operar nesses vetores diretamente
usando a
extensão pgvector, o que é muito legal.
E isso permite que você armazene seus
dados estruturados e vetoriais no mesmo
local.
Portanto, você sabe que pode ter não
apenas
pedaços de dados, mas também dados
estruturados.
Tecnicamente, você também poderia fazer
isso com JSON, mas
um pouco mais nativo com o Amazon Aurora.
Portanto, esse é o grande problema do
Aurora no contexto
da IA generativa e como um armazenamento
de vetores.
E o mais legal é toda
essa integração com o SQL.
Portanto, eu me lembraria dessa.
Isso pode ser apropriado para sistemas RAG
pequenos
ou médios se você tiver principalmente
dados estruturados.
Portanto, é claro que o Aurora é mais uma
espécie de monólito.
Dimensionar isso pode ser um desafio um
pouco maior.
No entanto, se você tiver um sistema
pequeno ou médio
- e, convenhamos, a maioria de nós tem - e
seus dados forem, em sua maioria,
estruturados, essa pode
ser uma opção adequada para sua loja de
vetores.
Portanto, se estiver escolhendo um
armazenamento de
vetores, o Aurora com pgvector pode ser
a resposta se você tiver um sistema
RAG pequeno ou médio com dados
estruturados.
