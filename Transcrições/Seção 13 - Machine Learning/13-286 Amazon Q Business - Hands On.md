Ok, então vamos em
frente e
Então, vamos clicar em Amazon Q Business.
Comece agora.
E você pode receber um aviso sobre uma
região.
Portanto, escolha a região mais adequada
para você.
Por exemplo, se eu escolher Frankfurt,
você verá que não vai funcionar.
Portanto, preciso escolher, por exemplo, a
Irlanda.
Portanto, vamos criar um aplicativo
generativo que
usará nossa base de conhecimento interna.
Então, vamos criar esse aplicativo e
ele se chamará Q Business Demo.
E aqui para o acesso do usuário, para
manter
as coisas muito simples, vamos usar o
acesso anônimo.
Isso elimina grande parte da configuração
em torno dos usuários.
Então, por favor, me acompanhe com isso.
Na verdade, para essa prática, não me
siga.
Por favor, por favor, por favor, não faça
o que eu faço.
O hands-on é válido e mostra como usar
o Amazon Q, mas percebi, depois de
gravá-lo,
que o preço de consumo para fazer casos
de uso anônimos é de US$ 200 por
mês e você é cobrado imediatamente por
isso.
Portanto, se você quiser receber uma
cobrança
menor, precisará usar o Amazon Q Business
Light ou o Q Business Pro.
Mas isso inclui a funcionalidade de acesso
do usuário, e é muito difícil
configurá-la.
É por isso que eu quis manter
o vídeo simples e com acesso anônimo.
Portanto, para o acesso anônimo, os
usuários finais
têm a mesma funcionalidade; só que os
outros métodos são mais difíceis de
configurar.
Por isso, sou anônimo.
Não faça anônimo ou não acompanhe.
Apenas assistir ao vídeo é suficiente,
acredite, para
entender a capacidade do Amazon Q
Business.
Mas, por favor, se você estiver
acompanhando, esteja
pronto para pagar US$ 200 por um mês.
Portanto, isso foi doloroso para mim.
Ok, eu já o avisei o suficiente.
Agora vamos voltar ao vídeo.
Obviamente, isso não é bom para o acesso à
produção, mas para uma demonstração, isso
é perfeito.
Em seguida, vamos criar
esse aplicativo aqui mesmo.
E agora meu aplicativo foi criado.
Então, vamos visualizar a experiência na
Web aqui mesmo.
Na verdade, eu clico nele e terei
acesso ao bate-papo do Q Business.
Então, aqui está um bate-papo, estou no
modo visitante
e pergunto: "O que é a World Wide
Web?" E, como você pode ver agora, ele
diz: "Bem, peça ao seu administrador de TI
para adicionar fontes de dados". Portanto,
não temos
nenhuma fonte de dados, então vamos
adicionar uma.
Portanto, no lado esquerdo,
clique em Fontes de
dados, adicione um índice
e conecte as fontes
de dados, e pronto.
Portanto, nenhum índice foi adicionado a
esse aplicativo.
Vamos adicionar um índice.
Portanto, um índice custa algum dinheiro,
mas
usaremos um tipo de índice inicial.
Bom para prova de conceito,
desenvolvimento e testes.
E para um número de unidades é a
quantidade de
documentos que podemos ter em nossa fonte
de dados.
Escolheremos apenas uma, que é a menor
quantidade de
unidades, ou seja, 20.000 documentos ou
200 megabytes,
o que vier primeiro, o que é suficiente.
Então, vamos criar esse índice.
E isso pode levar algum tempo,
aproximadamente 20 minutos para ser
concluído.
Ainda assim, vamos rolar a tela para
baixo e saber mais sobre as opções.
Portanto, agora precisamos adicionar uma
fonte de dados.
Então, vamos clicar em Add data source
(Adicionar
fonte de dados) e podemos dar uma olhada
nas diferentes opções às quais temos
acesso.
Portanto, é nisso que o Amazon
Q Business baseará seu conhecimento.
Portanto, o mais popular é o Amazon
S3, e é esse que vamos usar.
Mas você tem opções diferentes.
Então você tem Asana, Box, Dropbox,
GitHub, Google Drive, Google Calendar.
Ou seja, muitas das informações que estão
em
sua empresa podem ser usadas como fonte
de informações para o Amazon Q Business.
Portanto, se você tiver todas as suas
informações
no SharePoint, talvez queira configurar o
SharePoint como
uma fonte, mas vamos simplificar as
coisas.
E, por enquanto, usaremos o Amazon S3.
Então, clicamos nele e o chamaremos
de My S3 Knowledge Base.
Eu desço a tela.
Precisamos selecionar uma função IAM,
portanto,
usaremos uma nova função de serviço,
recomendada, e ela será configurada
automaticamente.
Perfeito.
Agora, o escopo de sincronização.
Então, onde está o nosso bucket S3, onde
os dados são armazenados? Vamos procurar o
Amazon
S3 e, no momento, não temos nenhum.
Então, vamos para o Amazon S3 e criarei
um bucket de base de conhecimento como
este, mas desta vez não em us-east-1.
Vou selecioná-lo em eu-west-1, que
é onde estou no momento.
Então, vamos criar um bucket e darei
a ele o nome de eu-west-1.
O restante é o mesmo.
Vou criar esse bucket e
ele será criado na região
adequada, agora na Irlanda.
Isso é perfeito.
E para os arquivos, vou ter em meu
balde exatamente o mesmo arquivo de antes.
Então, deixe-me fazer o download do
arquivo Evolution of the Internet.
Perfeito.
E vou fazer o upload de volta para esse
balde.
Então, vamos fazer o upload.
Então, agora selecionei meu arquivo
e cliquei em Upload.
Tudo bem, então estamos prontos para
começar.
Portanto, neste balde aqui, temos este PDF
detalhado sobre a evolução da Internet.
Vamos atualizar o escopo de sincronização,
selecionar
meu bucket, este aqui, e escolhê-lo.
O tamanho máximo de um único arquivo é de
50 megabytes.
Não tocaremos em nenhuma dessas opções
avançadas.
Selecionaremos uma sincronização completa
e
a programação da sincronização
completa será sob demanda.
Isso é apenas para que possamos ter
um botão sincronizar agora e começar.
Mas, obviamente, na produção, talvez você
queira ter apenas uma sincronização para
conteúdo novo, modificado ou excluído, e
talvez queira que ela seja executada,
por exemplo, de hora em hora.
A propósito, meu índice já foi criado,
portanto, estamos prontos para este
tutorial.
Então, vamos em frente.
Vamos clicar em Add data source (Adicionar
fonte de
dados) e ele diz que, como estamos
habilitando o
acesso anônimo para o Q Business Demo, ou
seja,
sem usuários, podemos acessar as fontes de
dados sem
autenticação e, portanto, o Amazon S3
estará acessível publicamente.
Isso é bom para este tutorial de
demonstração.
Obviamente, essa não é uma configuração de
produção, é apenas para mostrar a você
a capacidade do Amazon Q Business.
Portanto, minha fonte de dados foi criada
e vou fechar todos esses pop-ups, e
você pode clicar em Sync agora
para sincronizar o que estiver no
seu bucket S3 com o índice.
Isso pode levar de alguns minutos a
algumas horas.
Acho que levará menos tempo, porque
temos apenas um documento, mas tudo
o que pertence ao nosso bucket
S3, ou seja, toda a base
de conhecimento, será sincronizado no
índice,
e esse índice poderá ser aproveitado
por nossa fonte de dados.
Portanto, vamos esperar que a
sincronização esteja acontecendo.
Ok, levou um pouco de tempo, mas aqui
estamos.
Temos um item sendo digitalizado e ele já
foi indexado.
Portanto, o que vai acontecer agora é que,
se eu voltar à Amazon Q Business
e perguntar: "O que é a World
Wide Web?", espero obter uma resposta
melhor.
E obtemos informações melhores.
Portanto, ela foi inventada por Tim
Berners-Lee, em 1989, e temos as
fontes que estão vinculadas diretamente ao
PDF em meu balde de demonstração
com a passagem específica da
qual ela foi realmente citada.
Portanto, isso é muito bom.
Portanto, temos os eventos, as fontes e
assim por diante.
Os eventos informam o que aconteceu
durante as
consultas e para que a resposta ocorresse.
As fontes informam quais documentos foram
usados.
E você também pode dar um feedback
sobre uma boa resposta, uma resposta ruim
ou até mesmo copiar a resposta.
Mas se você perguntar, por exemplo, "Me dê
uma receita de chili?", ele dirá: "Bem,
ouça,
não encontrei nenhuma resposta com base na
sua
base de conhecimento". Portanto, no
momento, o Amazon
Q Business está configurado para me dar
apenas
respostas baseadas em minhas fontes de
dados.
Você pode alterá-lo, se quiser, com isso
aqui
em torno dos controles administrativos e
das proteções.
Portanto, aqui, em vez de permitir que o
Amazon Q retorne ao conhecimento do LLM,
se
você definir isso como ativado e, na
verdade, não posso fazer isso agora porque
não tenho acesso a essa opção, mas
se você definir isso como ativado,
provavelmente
se você tiver um usuário ativado, por
exemplo, poderá retornar ao conhecimento
do LLM.
Mas isso pode não ser desejável.
Talvez você só queira obter respostas
com base em seu conhecimento interno.
Aqui também há controles para controles
específicos de tópicos.
Portanto, você pode estabelecer algumas
barreiras em
torno de algumas questões que talvez não
queira ver respondidas pelo Amazon Q,
mas isso lhe dá uma ideia.
Você pode adicionar quantas fontes de
dados quiser,
cerca de 50 fontes de dados por
aplicativo,
configurá-las e obter essa base de
conhecimento
interna com IA internamente em sua
empresa.
Espero que tenham gostado e
nos veremos na próxima palestra.
E não se esqueça de realmente
excluir seu aplicativo, pois há um
custo contínuo para ter um índice.
Muito bem, então é isso.
Espero que tenham gostado e nos
vemos agora na próxima palestra.
