serviço Ground Truth do SageMaker.
Esse é um produto relativamente novo da
Amazon.
E o que é isso? Bem,
é basicamente uma maneira de usar
humanos para rotular seus dados.
E eu meio que tive dificuldade em
saber onde colocar isso no curso.
No final, acabei colocando-o na engenharia
de recursos.
Porque, fundamentalmente, tudo se resume
a lidar com dados ausentes.
E, nesse caso, trata-se mais de rótulos
e recursos ausentes na maioria das vezes.
Mas você poderia, na verdade, aplicar
isso também aos recursos ausentes.
Basicamente, a ideia é que, se você tiver
dados ausentes que possam ser inferidos
facilmente por
um ser humano, o Ground Truth permite que
você entregue essas tarefas a seres
humanos reais
para que preencham os dados ausentes para
você.
E o exemplo mais comum disso é
o mundo da classificação de imagens.
Assim, por exemplo, se eu estiver
treinando um
novo modelo de classificação de imagem,
para treiná-lo,
alguém terá que passar por todas essas
imagens
de treinamento e marcá-las com o que
realmente
há nelas, certo? Isso não será
necessariamente
uma coisa fácil para um computador fazer.
Por exemplo, nesta imagem, alguém
classificou
a imagem como sendo de um
jogo de basquete ou de futebol.
Alguém precisa passar por isso e fazer
todo esse trabalho.
Que tipo de pássaro é
esse? Onde estão os pássaros
nessa imagem? Coisas desse tipo.
Assim, a Ground Truth gerenciará uma frota
de seres humanos que analisarão e
rotularão
seus dados para fins de treinamento.
Portanto, se você tiver um conjunto de
dados
enorme, como um monte de fotos, e precisar
de rótulos, às vezes os seres humanos são
a melhor maneira de obter esses rótulos.
A Verdade Fundamental é o que gerencia
esse processo para você.
Mas isso é mais do que apenas gerenciar
os seres humanos que rotulam seus dados.
O que diferencia o Ground Truth é que ele
cria
seu próprio modelo à medida que esses
rótulos chegam.
Portanto, esse modelo está aprendendo à
medida que recebe
mais e mais dados de rótulos dos humanos.
E, com o tempo, ele só enviará rótulos
para
os humanos sobre os quais não tem certeza.
Assim, com o passar do tempo, à
medida que receber mais e mais rótulos
dos rotuladores humanos, ele criará um
modelo
próprio e somente os casos ambíguos serão
enviados aos rotuladores humanos daqui
para frente.
Assim, esse modelo se desenvolve ao longo
do tempo, fica cada vez melhor, e
somente as coisas sobre as quais
o modelo não tem certeza são
de fato entregues a seres humanos.
Isso acaba reduzindo o custo de seus
trabalhos de
rotulagem em até 70%, o que é bastante
significativo.
Quem são essas pessoas? Bem, você
tem diferentes opções de quem
o Ground Truth pode usar.
Uma delas é simplesmente usar a força de
trabalho da Amazon Mechanical Turk.
Trata-se de uma enorme força de trabalho
de pessoas
em todo o mundo que rotularão seus dados e
farão uma série de outras tarefas simples
para
você por uma quantia muito pequena de
dinheiro.
Você também pode optar por terceirizá-lo
para sua própria equipe interna.
Portanto, se estiver lidando com dados
muito
confidenciais, isso pode fazer sentido
para você.
E também existem empresas de rotulagem
profissional
que não fazem nada além de ter
uma frota de seres humanos que rotulam
dados de treinamento para ganhar a vida.
Portanto, se você quiser alguém que seja
um
pouco mais especializado nesse tipo de
coisa, pode
gastar ainda mais dinheiro e usar um
deles.
Agora, há outras técnicas além do uso de
humanos
para gerar rótulos de treinamento que você
não tem.
Outra opção seria usar o serviço de
reconhecimento da
AWS, sobre o qual falaremos mais adiante
no curso.
Basicamente, trata-se de um serviço do AWS
para reconhecimento de imagens.
Portanto, se você precisar classificar
imagens, isso pode ser feito
para criar rótulos ou até mesmo dados de
recursos.
Talvez você tenha apenas um recurso em seu
conjunto
de dados para o que está nessa imagem.
O reconhecimento tem um modelo
pré-treinado para os tipos
mais comuns de objetos que você pode
simplesmente usar.
Portanto, se você estiver usando apenas
classificações
de objetos gerais no mundo, o
reconhecimento poderá fazer isso para
você.
Se estiver lidando com informações
textuais em vez
de imagens, o Comprehend pode ser útil.
Basicamente, esse é um serviço da AWS.
Você está fazendo análise de texto e
modelagem de tópicos.
Dessa forma, você poderia gerar
automaticamente tópicos
ou sentimentos para um determinado
documento.
Portanto, essa pode ser uma maneira de
criar rótulos
e talvez até recursos de treinamento
adicionais, certo?
Portanto, esse é outro exemplo de
engenharia de
recursos em que você pode gerar recursos
adicionais
em seu modelo usando algo como o
Comprehend.
Portanto, se eu tiver um documento, talvez
possa
usar o Comprehend para gerar novos
recursos
que incluam o tópico desse documento ou
o sentimento que ele representa, e essas
podem ser informações úteis para o
treinamento
e o modelo de aprendizado de máquina.
É por isso que esta seção
trata da engenharia de recursos.
Na verdade, você pode aplicar essas
técnicas
de uso de serviços existentes ou até
mesmo de seres humanos para gerar mais
informações que seu modelo possa usar.
Na verdade, qualquer modelo pré-treinado
ou técnica de
aprendizagem não supervisionada pode ser
útil para gerar
novos rótulos de treinamento ou até mesmo
novos
recursos de treinamento em seu conjunto de
dados.
Portanto, o Ground Truth é bastante
simples,
mas se ainda for muito difícil para
você, há algo chamado Ground Truth Plus,
em que alguém faz tudo para você.
E é uma solução pronta para uso, na qual
você basicamente contrata alguém por meio
da AWS para
configurar tudo e gerenciar todo o projeto
para você.
Portanto, na documentação, eles chamam
isso de
nossa equipe de especialistas em AWS.
Não sei bem de onde eles vêm,
mas essas pessoas gerenciam o fluxo
de trabalho, configuram tudo para você
e gerenciam sua equipe de rotuladores.
Tudo o que você faz é preencher este
formulário que diz quem você é, o que
está tentando fazer em um nível elevado, e
eles entrarão em contato com você e
tentarão
resolver os detalhes e discutir o preço,
que
eles não divulgam publicamente, mas
imagino que não
seja barato devido a esse tipo de
tratamento
de luva branca que eles dão a você.
À medida que eles configuram as coisas e
começam
a receber resultados de seu exército de
rotuladores,
você pode acompanhar o progresso deles por
meio
do portal do projeto Ground Truth Plus,
onde
eles fornecem alguns gráficos práticos que
mostram como
está o progresso e quais são os
resultados.
Quando eles finalmente terminarem, você
receberá os dados
do rótulo de volta do S3, mas
não há muito o que falar aqui.
Basicamente, é uma forma de transferir
todo o
problema de rotular seus dados para outra
pessoa.
Ground Truth Plus se você estiver disposto
a pagar por ele.
