geração aumentada de recuperação ou RAG no
Bedrock.
Em Bedrock, isso é chamado de base de
conhecimento.
Portanto, no lado esquerdo aqui, quando
você estiver
no painel do Bedrock, vá para ferramentas
do
construtor e clique em bases de
conhecimento.
Isso nos proporcionará uma maneira muito
fácil de criar um
armazenamento vetorial a partir de algum
documento ou conjunto de
dados e consultá-lo em um sistema do tipo
RAG.
Então, vamos clicar em criar base de
conhecimento
depois de ler a visão geral aqui.
Assim, você pode ver que há uma série de
coisas
que podem ser feitas com as bases de
conhecimento.
Você pode fazer upload de um documento e
conversar com ele.
Você pode criar uma base de conhecimento,
um armazenamento de vetores subjacente.
Você pode testá-lo e usá-lo em um
aplicativo real ou, como faremos mais
adiante, usá-lo em um agente maior.
Então, vamos começar clicando em criar
base de conhecimento.
Há vários botões para escolher aqui
e daremos um nome a ele.
Portanto, o que fiz foi fornecer o texto
de
um livro que escrevi há muitos anos sobre
trabalho
autônomo, e vamos usá-lo como nossa base
de conhecimento.
Por isso, vou apresentar esse livro
inteiro e faremos perguntas sobre ele.
Portanto, esse será o contexto que estamos
fornecendo ao nosso sistema e que ele
não conhecia antes, porque o modelo
subjacente
não tem conhecimento desse livro
específico.
Portanto, vamos chamá-lo de trabalho
autônomo.
E se você quiser dar uma descrição de
direção, pode fazê-lo no livro do Frank.
A propósito, ele está disponível
gratuitamente.
Portanto, vamos permitir que ele crie sua
própria função de IAM
aqui e usá-la em vez de ficarmos com uma
fantasia.
Se você quisesse fazer algo mais
restritivo,
poderia, mas não vou usar nenhuma tag.
Então, vamos seguir em frente e clicar em
next.
Muito bem, como você pode ver, precisamos
colocar isso
no S3 em algum lugar para que possamos
acessá-lo.
Então, vamos em frente e vamos para o S3.
Portanto, abra uma nova janela.
Vou dizer apenas para abrir um link, uma
nova guia
do S3, mas você pode simplesmente abrir
uma nova
guia e navegar até lá como quiser,
escolher algum
bucket ao qual tenha acesso e fazer o
upload.
Portanto, vamos criar um novo apenas para
fins de argumentação.
Ele precisa ser um nome exclusivo.
Vamos chamá-lo de sundog-book-rag.
Coloque seu próprio nome ali ou algo do
gênero, pois
os nomes dos buckets precisam ser
globalmente exclusivos, certo? E
não vou entrar em detalhes sobre como o S3
funciona,
mas todos esses padrões devem funcionar
bem para nossos propósitos.
Por isso, eu o chamo de sundog-book-rag.
Vamos em frente e encontrar isso.
Aqui está.
E faremos o upload dos materiais do curso,
book.txt.
Carregar.
Muito bem, agora está tudo pronto.
Então, de volta a Bedrock.
Você pode dar um nome à sua fonte de
dados.
Mais uma vez, vou chamá-lo de livro do
Frank.
E vamos procurar o arquivo que acabamos de
carregar.
Com certeza.
Aqui está.
Talvez seja necessário sair dessa tela
e voltar para a tela anterior
e vice-versa para que isso apareça.
Há um tipo de bug na interface do usuário
no momento.
Mas em sundog-book-rag, há o meu book.txt.
Então, vamos selecionar isso.
E podemos dar uma olhada nas configurações
avançadas.
Não precisamos delas, mas se você quiser
ter mais controle sobre a segurança,
poderá
usar sua própria chave KMS, se quiser.
Vou usar um padrão.
E também podemos escolher nossa estratégia
de chunking.
Vale a pena falar sobre isso.
Portanto, um problema que temos é como
dividir o conteúdo desse livro em vetores
individuais que estou armazenando no meu
armazenamento
de vetores subjacente? Portanto, há uma
estratégia
de fragmentação padrão que diz: bem, vou
dividi-lo em um determinado número de
tokens.
Portanto, o chunking padrão diz que tudo
será
dividido em, no máximo, 300 tokens, e cada
300 tokens será colocado em seu próprio
vetor.
Você pode imaginar que isso não é
exatamente
o ideal, certo? Seria melhor se cada um
desses vetores representasse algum tipo de
tópico coerente
ou algo assim, certo? Ao dividir em
pedaços,
você está apenas tirando a sorte grande
para saber se cada 300 tokens significa
algo significativo por si só ou não.
Mas essa parece ser a
estratégia padrão até o momento.
Portanto, o chunking padrão é de 300
tokens.
Você também pode selecionar chunking de
tamanho
fixo para especificar quais são esses
tokens
e também ter alguma sobreposição entre
eles.
Isso pode ser uma boa ideia se você
quiser ter algum contexto compartilhado
entre esses
vetores, o que pode ajudar um pouco.
Ou você pode dizer que não há chunking.
E se você quiser apenas dizer, ok, eu
mesmo já dividi em arquivos separados,
faça o
que eu lhe dei, pegue o que eu
lhe dei e não faça mais nada.
No entanto, é preciso garantir que o
número
de tokens em um bloco não exceda os
limites do modelo que você está usando.
E devo dizer que quero excluir
os dados subjacentes quando excluir essa
fonte de dados, pois não quero
ser cobrado por eles no futuro.
Então, vamos prosseguir e dizer próximo.
E agora precisamos decidir como
vamos realmente armazenar isso.
Agora, primeiro, você precisa de um modelo
de
embeddings, algo que possa pegar esses
pedaços e
convertê-los em vetores para você em
embeddings.
E, novamente, você precisa solicitar
acesso a
um modelo antes de poder usá-lo.
Portanto, se ainda não tiver feito isso,
vamos abrir outra nova janela aqui para
acesso ao modelo e verificar se você
solicitou acesso a um modelo de
incorporação.
Então, posso fazer, por exemplo...
Eu já tenho um, certo? Portanto, já
tenho o titan text embeddings V2.
Se você precisar comprar um novo, tente
algo diferente.
Portanto, novamente, você pode clicar em
disponível para solicitar um
desses modelos de incorporação depois de
ler os termos, solicitar
acesso, e isso deve ser adicionado a todo
o resto.
Portanto, quando eu clicar em próximo, ele
deverá dizer: "Vou solicitar
acesso a esse novo modelo de incorporação
e enviar isso".
Portanto, novamente, isso pode levar
alguns minutos e,
mais uma vez, talvez seja necessário
voltar à
interface do usuário para que isso
apareça.
Mas, como você se lembra,
eu já tinha acesso ao
titan text embeddings V2.
Em seguida, podemos selecionar quantas
dimensões queremos em cada vetor.
Portanto, vou manter o padrão aqui de
1024.
Novamente, isso é apenas a complexidade e
o tamanho
de cada vetor, o que lhe dá mais espaço
para incorporar o significado desse trecho
de texto.
E vou fazer a coisa mais fácil aqui
e deixar que ele configure um novo
armazenamento
de vetores de pesquisa aberto para mim.
Agora, a busca aberta, o Elasticsearch,
seja qual for o nome que
você queira dar, tem um armazenamento de
vetores, uma opção de modelo
de incorporação em que é possível fazer
buscas eficientes por vetores.
Então, vou dizer, ok, vá em frente
e faça um novo para mim.
Provavelmente não é uma boa opção para uso
em produção.
Se você tiver um servidor sem servidor de
pesquisa aberta
existente ou Aurora ou MongoDB ou Pine
Cone ou Redis,
qualquer que seja o armazenamento de
vetores que você
tenha, poderá apontá-lo para ele e fazer
isso aqui.
Mas vou criar um novo automaticamente,
pois
não quero me aprofundar em como
criar um servidor de pesquisa aberto.
Já que estou apenas brincando aqui.
Não vou me preocupar com redundância e
não vou me preocupar com minhas próprias
chaves de segurança gerenciadas pelo
cliente.
Então, vamos clicar em next.
E estamos quase prontos para começar aqui.
Portanto, basta revisar os detalhes.
Estamos criando uma nova base de
conhecimento chamada trabalho
autônomo com base nessa fonte de dados,
que é
o contexto do livro que carreguei no S3.
Usaremos o modelo titan text embeddings V2
embeddings com o tamanho de vetor de
1024 e criaremos seu próprio armazenamento
vetorial
sem servidor de pesquisa aberta para
armazená-lo.
Portanto, crie uma base de conhecimento.
E, desde que você não seja o usuário root,
ele deverá ser bem-sucedido.
Por algum motivo, o Bedrock não gosta
de trabalhar com usuários root no momento.
Portanto, estou conectado como um usuário
IAM com sua própria
conta, o que, de qualquer forma, é a
melhor prática.
Você não deve usar sua conta root para
fazer coisas.
Isso levará um pouco de tempo porque, nos
bastidores, ele está criando um
armazenamento de vetores
sem servidor de pesquisa aberta e criando
vetores
para tudo nesse livro usando o modelo de
incorporação que escolhi e vinculando tudo
isso
em um sistema que eu possa consultar.
Então, vamos voltar quando isso for feito.
Tudo bem, isso foi configurado.
Portanto, tenho meu armazenamento de
vetores e uma pesquisa
aberta que contém vetores associados a
cada bloco de
300 tokens do livro que forneci a ele.
Legal.
Agora, ele me alerta aqui que preciso
sincronizar isso antes de fazer qualquer
coisa.
Portanto, embora eu tenha configurado esse
banco de dados,
ainda não sincronizei a fonte de dados com
ele.
Portanto, ele ainda não foi adiante e
criou esses vetores e essas incorporações.
Então, vamos clicar em ir para fontes de
dados.
E, a partir daqui, posso selecionar a
fonte de dados do
livro do Frank e sincronizá-la para
realmente criar esses vetores.
E isso pode levar alguns minutos.
Portanto, mais uma vez, voltarei quando
isso for feito.
Tudo bem, isso não levou muito
tempo, então vamos brincar com isso.
Então, neste ponto, tenho uma base de
conhecimento,
que é apenas um armazenamento de vetores,
certo?
Portanto, ela tem o texto, novamente, do
meu
livro dividido em pedaços de 300 tokens
e criou vetores de incorporação que posso
usar para a pesquisa semântica dessas
informações.
Então, vamos brincar com ele para criar
uma espécie de sistema RAG de
demonstração.
Posso selecionar um modelo a ser usado
como modelo de base para esse sistema.
Anteriormente, solicitei acesso ao Claude
3 Sonnet.
Vamos usar isso.
Qualquer coisa a que você tenha acesso.
E agora, tenho esse tipo de sistema
de geração aumentada de recuperação pronto
que
consultará automaticamente esse
armazenamento de vetores sobre
meu prompt e recuperará o contexto
relevante
para o prompt e o incluirá no
prompt que é realmente enviado para o
Claude 3 Sonnet neste exemplo ou qualquer
modelo de fundação que você esteja usando.
Então, vamos experimentar.
Vamos fazer uma pergunta sobre meu livro.
Então, novamente, é um livro sobre
trabalho
autônomo e parte dele fala sobre uma
espécie de preparação para se tornar
autônomo.
Então, vamos perguntar: quais etapas devo
seguir
antes de tomar a decisão de me
tornar autônomo? E ela deve se
basear no contexto de meu livro.
Agora, o RAG, é claro, leva um pouco mais
de tempo
do que apenas usar o modelo de fundação em
si.
Ele precisa recuperar essas informações do
armazenamento de
vetores, neste caso, a pesquisa aberta, e
descobrir
como injetar tudo isso em meu prompt
e, em seguida, alimentar esse prompt
maior.
Ei, funcionou.
Portanto, ele diz coisas que são
consistentes com
o que eu disse em meu livro.
Portanto, isso é muito bom.
De fato, ele tem recomendações muito
específicas.
Eu provavelmente atualizaria isso se fosse
escrever isso novamente, mas
na época em que escrevi, tudo isso era
válido.
Ei, tem até citações, o que é bem legal.
E também pode mostrar detalhes da fonte.
O que isso faz? Ei,
dê uma olhada nisso.
Assim, ele realmente mostra quais partes
recuperadas
foram consideradas relevantes para aquela
pergunta.
Portanto, isso fornece informações sobre
os pedaços reais
de 300 tokens que ele escolheu como
contexto adicional para responder a essa
pergunta.
Muito legal.
Portanto, esses são os cinco trechos que
ele realmente optou por incluir na
consulta que foi enviada ao Claude.
Isso é fantástico.
E também mostra de onde ele veio.
Assim, podemos ver que ele, de fato,
extraiu isso das informações que carreguei
no
S3 para a minha base de conhecimento.
Legal, funciona.
Portanto, não vou excluir isso porque
usaremos
essa base de conhecimento em um sistema
de agentes mais adiante neste curso.
Mas você está acumulando custos ao deixar
isso de lado.
Portanto, se você não for passar
imediatamente
para a próxima seção do curso, para
evitar surpresas na sua conta da AWS,
é melhor encerrar o curso quando terminar.
Portanto, lembre-se de que definimos a
fonte de dados
para excluir a pesquisa aberta do banco de
dados
vetorial subjacente quando excluímos a
fonte de dados real.
Então, vamos voltar às bases de
conhecimento
aqui, clicar na base de conhecimento e,
se terminar, certifique-se de selecionar a
fonte
de dados e excluí-la, certo? E, quando
terminar, vá para a própria base de
conhecimento e exclua-a também, certo?
Portanto, um
pouco de limpeza para garantir que
você não receba nenhuma conta surpresa.
Mas como quero desenvolver esse exemplo e
criar
um agente usando essa base de
conhecimento, não
farei isso ainda, mas não se esqueça de
excluir isso quando terminar, ou você será
cobrado para sempre por esse banco de
dados de pesquisa aberto sob o capô.
Você não quer isso.
Mas isso foi muito legal.
Criamos um pequeno sistema RAG apenas na
interface do usuário aqui do Amazon
Bedrock.
Não é necessário código.
Isso é muito legal.
Mas, em algum momento, precisamos de
código.
Então, vamos falar sobre alguns
aplicativos
mais avançados que podemos criar com
base nessa base de conhecimento.
