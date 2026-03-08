a IA generativa e a AWS, portanto, vamos
começar colocando a mão na massa
imediatamente.
Certo? Portanto, no Bedrock, temos um
playground, se preferir, que nos permite
brincar com diferentes modelos de
fundação.
E, fundamentalmente, o Bedrock é esse
invólucro em torno de diferentes modelos
de fundação de diferentes fornecedores que
você pode usar para brincar, criar
aplicativos ou o que quiser fazer.
Portanto, se você acessar o console do
Bedrock aqui,
deverá ver um painel de teste aqui no
menu.
Vamos começar com o bate-papo e o texto
e explicar o que está acontecendo aqui.
Portanto, há dois modos diferentes
aqui: bate-papo e prompt único,
anteriormente chamado de texto.
O bate-papo, é claro, é apenas uma
conversa de bate-papo.
Você pode ir e voltar e desenvolver
o contexto do que falou anteriormente.
E esse contexto continua a se desenvolver
à medida que o bate-papo se prolonga.
Enquanto o prompt único é uma coisa
única, nós fazemos uma solicitação, ele
me dá uma resposta e pronto.
Você sabe, é isso.
Então, vamos começar com o bate-papo,
porque é
isso que a maioria das pessoas quer fazer.
A primeira coisa a fazer é selecionar um
modelo para conversar.
E você pode ver aqui que há um menu muito
bom.
E, novamente, o objetivo do Bedrock é
envolver
todos esses modelos diferentes e permitir
que
você interaja com eles de maneira
consistente.
Portanto, você pode até mesmo usar o
OpenAI, alguns dos modelos mais antigos,
o DeepSeek, se quiser fazer isso.
Eu gosto do Anthropic, portanto, vamos
usar
o Clause Sonnet 4, mas você
pode escolher o modelo que quiser.
E se você quiser um perfil de
inferência específico, também pode fazer
isso aqui.
Vou ficar com o Global Claude Sonnet.
Se eu quisesse a versão
americana, poderia fazer isso, mas
não importa, estamos apenas brincando.
Muito bem, vamos examinar essas
configurações.
Portanto, os prompts do sistema,
basicamente qualquer informação
consistente
que você queira dar a ele, se aplicam
a tudo o que você faz no bate-papo.
Voltaremos a esse assunto.
Raciocínio do modelo.
Então, isso é uma coisa nova, certo?
Portanto, se
eu quiser dar a ele uma tarefa mais
complicada,
esses modelos maiores são capazes de fazer
isso.
Assim, por meio de uma cadeia
de pensamento, ele pode realmente pegar
uma tarefa complicada, dividi-la em
subtarefas
menores e, em seguida, juntá-las todas.
É isso que queremos dizer com raciocínio.
Portanto, trata-se basicamente de um
processo de várias
etapas em que ele pega seu prompt
complicado,
divide-o em etapas para alcançar o que
você deseja e, em seguida, executa essas
etapas específicas para fornecer uma
resposta final.
E ao habilitar o raciocínio de
modelo, habilitamos esse tipo de
comportamento,
que obviamente custa mais, mas se
você for fazer coisas mais
complicadas, talvez valha a pena.
Podemos especificar qual é a duração
máxima do raciocínio,
ou seja, até que ponto quero que você
pense, certo? Portanto, você tem controle
sobre isso.
Obviamente, há um equilíbrio
entre complexidade e custo.
E ele também informará o que estava
fazendo ao longo do caminho, mas
não vou dar a ele nada
tão complicado, portanto, vou desativar
isso.
Máximo de tokens de saída, descobri que
isso é mais uma sugestão do que
uma regra em alguns modelos, mas se
você quiser ter alguma influência sobre
o tamanho da resposta final, é
aqui que você deve fazer isso.
Você também pode definir suas próprias
sequências de parada personalizadas.
E se você tiver um modelo que vai
gerar uma sequência específica de
caracteres, talvez você
ajuste isso ou algo assim, ou se for
o seu próprio modelo, essa seria uma forma
de especificar que eu quero que você
desligue quando atingir a sequência de
caracteres.
Aleatoriedade.
Muito bem, este é um pouco mais
complicado.
Portanto, há duas opções aqui: temperatura
ou P superior.
Então, com a temperatura, vamos voltar um
pouco atrás.
Portanto, os modelos de linguagem grandes,
se
eu realmente simplificar demais, estão
apenas prevendo
a próxima palavra em uma frase
repetidamente.
E, nesse processo, para cada palavra
que está sendo prevista, ele tem
uma lista de candidatos que pode
escolher como a próxima palavra
apropriada.
A temperatura é a quantidade de
aleatoriedade que existe nessa decisão.
Portanto, com uma temperatura de zero, ele
sempre
escolherá o resultado principal, o que
geralmente é
o que você quer, mas se quiser que
as coisas sejam um pouco mais malucas, um
pouco mais aleatórias, talvez seja melhor
mudar isso.
O Top K é basicamente quantas palavras ele
tem
para escolher? Portanto, quando estou
gerando candidatos para a
próxima palavra em uma frase, tecnicamente
eles são
tokens, não palavras, mas, seja como for,
essa
é a quantidade que ele tem para escolher.
E 250 é o que isso é por padrão.
Como alternativa, eu poderia mudar,
poderia
especificar a aleatoriedade e a
diversidade
do resultado por P superior.
E, novamente, temos um top K de quantos
estamos escolhendo,
mas, nesse caso, o top P se refere ao
limite de probabilidade de o próximo token
estar correto.
Então, em vez de dizer que tenho 250
candidatos, qual é o grau de aleatoriedade
que
quero ter ao escolher entre eles? Estou
dizendo
que este é o limite de quão bom
um candidato precisa ser, em primeiro
lugar.
Tudo bem? Portanto, não acho que isso
seja algo de que você precisará
para o exame, mas estou apenas
explicando o que esses parâmetros
significam.
Basicamente, ambas são formas de controlar
o quão estranhos, criativos, diferentes e
não reproduzíveis serão seus resultados.
As grades de proteção serão abordadas mais
adiante no curso.
Basicamente, há maneiras de ter esses
mecanismos que dizem
que você não deve enviar informações
pessoais identificáveis,
nem emitir informações pessoais
identificáveis, nem dizer palavrões
ou coisas sobre as quais não queira falar.
É para isso que servem as grades de
proteção.
Estamos chegando lá, mais tarde.
Muito bem, vamos ver se funciona.
Então, vamos dar uma olhada.
Algo simples, como qual é
o sentido da vida? Boop.
Tudo bem, acho que essa pergunta já foi
feita antes,
então você sabe que ela vai me dar uma
resposta muito genérica que diz que não há
resposta.
E como este é um bate-papo, posso me
basear nisso, certo? Então, como estou no
modo
de bate-papo, posso dizer algo que se
baseie no contexto dessa conversa anterior
e
posso dizer algo como, para que serve
- não sei, escolha sua filosofia favorita.
Niilistas.
E como ele tem o contexto do bate-papo
anterior, ele sabe a que estou me
referindo.
Espero que sim.
Sim, é verdade.
E ele diz, bem, nesse caso, não há
significado,
mas ninguém realmente acredita nisso, yada
yada, tanto faz.
Ok, isso é um bate-papo.
E, novamente, a única diferença em relação
ao prompt único
do modo texto é que não há histórico de
bate-papo.
Mas vamos testar isso rapidamente.
Então, novamente, vou selecionar um
modelo.
Agora estamos na terra do prompt único.
Vamos nos ater ao antrópico.
E só para mostrar um prompt do sistema em
ação, vamos
dizer que ele sempre responde no estilo de
um pirata.
Portanto, agora tudo o que eu disser
receberá uma resposta em linguagem pirata.
Muito bem, agora também quero mostrar que
você pode misturar e combinar suas
entradas.
Assim, podemos fazer upload de um arquivo.
Esse é um modelo multimodal e, se
acessarmos
os materiais do curso, você verá um
arquivo CFAS bylaws rev9 dot doc X.
Assim, posso usar um bom e
velho documento do Word para isso.
Trata-se apenas de um documento do Word
que
contém os estatutos de um clube de
astronomia
do qual fui presidente por alguns anos.
Então, na verdade, fiz isso no mundo real
porque, às vezes, é meio difícil
entendê-los.
Assim, posso dizer: "Ei, Claude, resolva
isso para mim".
Preciso saber quais são os requisitos de
quorum
para uma votação anual para a diretoria.
E, com sorte, ele vai ingerir esse
documento
e basear sua resposta no que encontrar.
Vamos descobrir.
Ah, e por falar nisso, ele também
responderá no estilo de um pirata.
Sim, ele, ele.
Eu adoro isso.
Sim, eu sou forte.
Dicas de chapéu de tricô.
Belo toque.
Sim, basicamente está dizendo que sim,
precisamos fazer isso
na reunião ordinária de outubro e
precisamos de um
quórum de 15 membros e dois membros do
conselho.
E é isso mesmo.
Você sabe, eu li o estatuto e isso está
correto.
Portanto, bom trabalho, pirata Claude.
Muito bem, vamos fazer algo com
um tipo diferente de modalidade.
Então, de volta a Bedrock.
E, desta vez, vamos para o playground de
imagens.
Você também pode fazer a detecção
de marca d'água e outras coisas,
mas vamos parar nas imagens.
Portanto, o playground de imagem e
vídeo significa gerar imagens ou vídeos.
Portanto, primeiro precisamos de um modelo
de imagem ou vídeo.
A Amazon tem algumas opções interessantes
que você pode escolher.
Portanto, os modelos de vídeo podem ser um
pouco caros.
Portanto, você provavelmente está com um
orçamento
limitado, não vou mandá-lo para lá, mas
gerar uma imagem não deve custar muito.
Vamos fazer o Nova Canvas.
E podemos fazer sob demanda ou provisionar
a
taxa de transferência para o modelo de
inferência.
Portanto, sob demanda significa que ele
estará,
você sabe, girando todos os recursos
necessários
para criar essa imagem e girando-a
novamente.
Mas se eu quisesse gerar imagens
basicamente
sem parar, 24 horas por dia, 7
dias por semana, talvez fosse mais barato
provisionar a taxa de transferência para
isso
antecipadamente, mas definitivamente não
quero gastar isso
no momento, portanto, será sob demanda.
Tudo bem, então o que queríamos fazer,
veja,
há todo tipo de coisa que podemos fazer.
Podemos gerar uma imagem, podemos fazer
variações de
uma imagem existente, podemos remover um
objeto, substituir
um objeto em uma imagem, substituir o
plano
de fundo, remover o plano de fundo.
Muito legal.
Assim, eu poderia carregar uma imagem e
fazer com que ela
fosse modificada ou simplesmente criar uma
nova imagem do zero.
Então, para facilitar a vida,
vamos fazer um do zero.
Você também pode ter um prompt negativo
que
diga a ele o que não deve fazer.
Portanto, se você quiser dizer: "Ei, não
gere imagens que
tenham esses atributos", é aí que eu
diria: "Se eu
quiser um tamanho de imagem específico,
posso fazer isso aqui".
Número de imagens que eu quero, ooh,
ele pode me dar várias para escolher.
Também posso especificar uma paleta de
cores específica.
Isso é muito legal.
Se eu tiver uma espécie de diretrizes de
marca
ou uma paleta de cores para um site
existente
ou algo assim, posso adicionar isso ali
mesmo.
Muito legal.
E também posso fornecer uma imagem de
condicionamento
para dar um exemplo do que eu quero.
A força do prompt é basicamente o
grau de aderência ao seu prompt.
Portanto, você pode pensar nisso como uma
alavanca de criatividade.
Portanto, se eu diminuir essa força, ela
poderá sair um pouco mais dos trilhos
e, às vezes, você quer isso.
Seed é basicamente a semente aleatória.
Portanto, se eu quiser obter resultados
reproduzíveis, quero ter certeza
de que tenho uma semente consistente todas
as vezes.
Vamos ver se funciona.
Portanto, escreva um prompt, ok, crie
uma imagem em estilo de
desenho animado de uma galinha.
Vamos fazer com que o frango faça algo
estranho.
Usando fones de ouvido.
Pronto.
Vamos ver o que ele pode fazer.
E eu escolhi três imagens,
portanto, terei três para escolher.
Isso foi muito rápido.
Na verdade, isso foi muito rápido.
E lá estão as minhas galinhas usando fones
de ouvido.
Eles não parecem felizes com
isso, não é? Puxa vida.
Tudo bem.
Mas sim, esse é o Bedrock em ação,
pessoal.
Apenas brincando um pouco no playground de
imagens e no playground de texto.
E, obviamente, você pode ver nesse menu
que
há muito mais coisas que você pode fazer.
Vamos nos aprofundar em muitas dessas
coisas
e criar aplicativos reais com base em
nossos modelos, e não apenas fazer
fotos de galinhas, portanto, fique atento.
Mas, sim, há o Bedrock
para você pela primeira vez.
