de chunking é uma maneira de otimizar
a
fase de recuperação de sua base de
conhecimento
ou sistema de geração aumentada de
recuperação.
Outra é otimizar os tamanhos reais
dos próprios vetores de incorporação.
Então, se você se lembra, esses vetores de
incorporação
que estavam traduzindo nossos pedaços de
texto em uma
espécie de representação do significado
desses pedaços de texto.
Mais especificamente, a proximidade entre
esses
vetores representa a semelhança semântica
entre esses trechos de textos.
Portanto, você precisa descobrir qual é o
tamanho que esses vetores realmente
precisam ter.
Se forem muito grandes, você estará
desperdiçando
espaço e gastando dinheiro armazenando
mais informações
do que o necessário e enviando mais
dados pelo cabo do que o necessário,
certo? Mas se os vetores forem muito
pequenos, você perderá parte desse
significado
importante, parte dessas informações
importantes e
isso afetará a qualidade da recuperação.
Portanto, vetores menores significarão
menos dimensões por bloco e
custará menos para armazenar e processar
esses dados.
Mas também haverá uma troca
com seu desempenho de recuperação.
Agora, o Titan tem o padrão de 1024 ou
mais dimensões.
Já vi o número ser citado como 1024 ou
1536.
Talvez esteja mudando, mas é muito, certo?
Portanto, se
você estiver armazenando um pedaço de 300
caracteres, talvez
esteja gastando mais dinheiro armazenando
esse vetor de
incorporação do que o próprio pedaço de
dados.
Portanto, antes de mais nada, pergunte a
si
mesmo: qual é o tamanho dos meus blocos?
Eu realmente preciso de tantas informações
para
codificar o que isso significa? E isso
também pode ter a ver com o
domínio com o qual você está lidando.
Portanto, dependendo do tipo de dados que
você
está armazenando, talvez seja algo bem
simples.
Você sabe, não há muitas categorias de
coisas que possam ser semelhantes entre
si.
Nesse caso, talvez você possa usar um
tamanho
de dimensão menor do que um maior.
Portanto, se os conceitos semânticos que
você está
pesquisando forem complexos, você poderá
se beneficiar de
tamanhos de vetor maiores em seus
embeddings.
Mas, se não for o caso, talvez você possa
experimentar com modelos menores e
economizar alguns dólares.
O que quero dizer com embeddings esparsos
e densos? Esse
termo é usado de maneiras diferentes, mas,
tecnicamente, um
vetor esparso é aquele que é quase todo
vazio.
É por isso que ela é esparsa.
Um exemplo é a codificação one-hot.
Então, digamos que eu tenha um vetor que
representa o tipo de animal que algo é.
Talvez eu tenha uma dimensão para cada
animal que
conheço e tenha apenas um na dimensão que
está
realmente correta e um zero em todas as
outras, certo? Esse é um exemplo muito
extremo.
Mas, você sabe, um vetor que representa
uma galinha pode
ter apenas um na dimensão da galinha e um
zero na dimensão da lula, e assim por
diante.
E um bonobo teria um um na dimensão
bonobo, mas um zero na dimensão lêmure,
certo?
Esse é um exemplo de um vetor esparso.
Muito semelhante, mas obviamente há muito
espaço
desperdiçado e isso é um problema.
O que você vê quase o tempo
todo, como eu nunca vi nada além
disso pessoalmente, é uma incorporação
densa.
Portanto, no contexto da IA generativa,
normalmente
temos essas dimensões de ponto flutuante
em
que, juntas, essas dimensões representam
um vetor
no espaço multidimensional que representa
o
significado semântico desse pedaço de
dados.
Geralmente é isso que você usa.
Agora eles podem ser menores porque
não há muito espaço desperdiçado.
Ele está realmente empacotando essas
informações ali, certo? É por
isso que o chamamos de vetor de
incorporação denso.
Agora, há uma troca aqui.
Um vetor esparso lhe dará
fatores de similaridade maiores.
Portanto, você vê isso sendo muito usado
em sistemas
de recomendação, nos quais estamos
tentando dizer, ok, aqui
estão as coisas que essa pessoa comprou,
aqui
estão as coisas que essa outra pessoa
comprou.
Qual é a semelhança entre eles? E
você pode obter algumas métricas de
similaridade
realmente limpas usando esses vetores
esparsos.
Mas os vetores densos serão muito mais
eficientes, tanto na memória quanto em
geral.
Agora, há maneiras de compactar vetores
esparsos
e vemos isso nos sistemas de recomendação.
No entanto, é um pouco difícil fazer isso
em uma GPU.
Portanto, você sabe, não se vê tanto isso
na IA generativa.
Espere, qual é o fator de similaridade?
Do que estou falando? Então, um fator
de similaridade é apenas uma medida
de quão próximos esses vetores estão.
Então, já falamos sobre, você sabe,
embeddings
que são próximos um do outro,
representando
duas coisas com um significado semelhante.
Como podemos medir isso de fato? Bem, isso
é o
que é um fator de similaridade, e um fator
muito comum é o fator de similaridade do
cosseno.
É apenas o cosseno entre esses dois
vetores.
E você pode fazer isso no espaço
multidimensional.
Não precisa ser apenas X e Y, a matemática
é a mesma.
E se você se lembra da trigonometria do
ensino médio,
o cosseno está relacionado ao ângulo entre
os dois vetores.
E ele é configurado de tal forma
que, se dois vetores forem iguais,
você terá um cosseno de um.
Se forem totalmente diferentes, será um
cosseno de zero.
Portanto, é basicamente uma medida de quão
próximos esses
vetores estão uns dos outros nesse espaço
de incorporação.
Outra coisa boa é que o
cosseno tem uma suavidade agradável.
Portanto, ele não tem apenas esses pontos
agudos nessas
descontinuidades, ele tem um movimento
suave para cima e
para baixo, o que o torna um pouco
mais útil também do ponto de vista
matemático.
Similaridade de cosseno, lembre-se disso.
Além disso, outra maneira de otimizar
sua recuperação é incorporar metadados
junto
com seus vetores de incorporação.
Assim, você pode alimentar uma base de
conhecimento com mais do
que apenas o texto bruto do trecho e
receber de
volta esses vetores de incorporação em seu
armazenamento de vetores.
Normalmente, você armazena o bloco em si e
seus vetores de incorporação, para que
possa procurar
esses blocos por suas incorporações,
certo? Mas você
também pode passar metadados, e isso é
importante.
Portanto, se você passar um arquivo
metadata.json para
a sua base de conhecimento ao criá-la,
poderá especificar metadados adicionais em
cada parte.
E como isso está sendo sinalizado como
metadados e não
como uma coluna de conteúdo, a base de
conhecimento
saberá que não deve tentar dividir isso em
pedaços.
Você sabe, esses serão apenas
metadados anexados a cada bloco.
Por exemplo, digamos que eu tenha um
livro sobre galinhas, voltando às
galinhas.
Portanto, posso ter uma passagem da
introdução desse livro
que diz que uma galinha é uma ave
domesticada
comumente criada para comer carne e ovos,
e
posso ter alguns metadados associados a
essa parte.
É da seção de introdução.
O livro é sobre biologia
e contém as seguintes palavras-chave:
frango, ave domesticada, carne, ovos.
Portanto, tudo isso pode ser associado a
esse bloco
e isso pode me permitir fazer uma espécie
de abordagem híbrida quando estou
procurando esse bloco
de dados no meu armazenamento de dados
vetoriais.
Então, quando estou procurando isso no
vetor de
incorporação, posso começar inicialmente
com essa semelhança semântica,
a distância entre esses vetores de
incorporação, mas
depois posso usar esses metadados talvez
para
ajustar esses resultados, talvez para
reclassificar esses
resultados com base na relevância dos
metadados
desse bloco para o prompt que está
chegando, o que é chamado de
reclassificação.
Falaremos sobre isso com um pouco mais
de detalhes mais adiante no curso.
Mas a ideia que quero que
você leve para casa é que
posso anexar metadados aos meus blocos,
além dos próprios vetores de incorporação,
e posso usar esses metadados para
otimizar ainda mais minha recuperação.
Em outros exemplos de metadados, você pode
incluir
o ID do documento original, que pode me
permitir voltar e obter o documento de
origem original e fazer algo com ele.
A categoria dessas informações pode ser
uma informação de controle de acesso,
talvez eu queira usá-la para garantir
que essas informações não sejam usadas
em determinados cenários, certo? A
linhagem
dos dados de onde eles vieram,
talvez eu precise documentar isso,
por exemplo, ao fornecer citações.
Portanto, se eu tiver uma parte dos dados,
posso
anexar metadados informando a origem
desses dados, e
talvez eu possa citar isso na minha
resposta
final do sistema ou qualquer contexto
adicional que
você queira anexar a essa parte do texto.
Portanto, você pode ver que os metadados
podem
ser muito importantes em sua loja de
vetores.
Você pode ter mais do que apenas o
vetor de incorporação e o texto bruto
real.
Você também pode ter informações sobre
isso
que podem ser recuperadas junto com ele
para melhorar ainda mais sua recuperação.
E a galinha aprova.
Observação rápida sobre como manter suas
bases de conhecimento atualizadas.
Então, como você se certifica de que ele
não está obsoleto? Isso também é
importante para
obter bons resultados com ele, certo?
Portanto, uma
ideia geral é que, se você tiver conteúdo
novo ou alterado, talvez haja algum tipo
de
gatilho de evento, como um evento S3, que
possa acionar uma função Lambda, que, por
sua
vez, pode acionar uma atualização em lote
da
sua base de conhecimento, certo? Assim,
talvez essa
função Lambda possa dar início à criação
de novos embeddings e você possa gerá-los
em lote para obter ainda mais eficiência.
Portanto, o diagrama aqui provavelmente
não é algo
que você realmente queira fazer na
prática.
A ideia é boa, mas o que vai
acontecer é que, se houver muitas
atualizações no
S3 e a função Lambda for acionada com
frequência, você não vai querer chamar
StartIngestionJob
no Bedrock repetidamente a cada segundo,
certo?
Isso deve se recuperar muito, muito
rápido.
Seria melhor fazer isso em lote usando
algo como
o AWS Batch e talvez o Event Bridge, além
disso, para enfileirá-lo e fazê-lo com
menos frequência.
Mas, conceitualmente, espera-se que você
entenda que talvez queira
usar uma função Lambda para iniciar as
atualizações
da sua base de conhecimento, e abordaremos
algumas
maneiras mais sofisticadas de fazer isso
mais tarde.
