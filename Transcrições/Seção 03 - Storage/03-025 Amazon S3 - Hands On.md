Então, aqui estou
Agora você notará que há uma região selecionada,
que é Europa, Estocolmo, eu-north-1.
E isso se deve ao fato de eu ter a seleção de região aqui.
Portanto, escolha a região em que deseja criar seu bucket e veremos
que o Amazon S3 ainda tem uma visão de
todos os seus buckets em todas as regiões.
Agora, há um tipo de balde que você pode ou não ver.
Portanto, se você estiver em algumas regiões em que
ele está disponível, verá a opção de uso geral ou diretório novo.
E, com o tempo, estará em mais regiões.
Se você não o vir em sua região, não há problema.
A opção que você deve
escolher, caso a veja, é a de uso geral.
E se você não vir essa opção, ela será
automaticamente de uso geral.
Portanto, não mexa
em nada e não se assuste se você não vir essas opções.
Os buckets de diretório são para um tipo específico de caso de
uso que não é abordado no exame,
portanto, não falarei sobre isso.
Portanto, se você vir a tela, escolha a finalidade geral.
Se não vir a tela,
está tudo bem, não se preocupe.
Ok, então você escolhe uma região e, em seguida,
precisa escolher o nome do balde.
Portanto, se você digitar um nome de bucket que já esteja ocupado,
por exemplo, testes,
e tentar criar o bucket, receberá um erro dizendo que
o bucket com o mesmo nome
já existe.
Portanto, o nome do seu bucket deve ser exclusivo em todas as regiões
e em todas as contas já criadas na AWS.
É por isso que nomeio meus baldes com
algo muito, muito pessoal.
Por exemplo, poderia ser Stephane e, em seguida, demo, S3, e geralmente
adiciono o número da versão, v5, porque
tenho criado esse vídeo muitas e muitas vezes
à medida que a interface muda.
Portanto, o stephane-demo-s3-v5 deve estar disponível e não deve apresentar
erros.
Mas se alguém já o tiver usado,
precisarei alterar o nome.
Certo, então o próximo passo é a propriedade do objeto.
No momento, você tem a ACL desativada.
Isso é recomendado.
Essa é uma configuração de segurança.
Não se preocupe com isso. Vamos deixá-lo como padrão.
Agora, para bloquear o acesso público a esse bucket,
novamente, deixaremos isso ativado.
Portanto, bloquearemos todo o acesso público
e queremos ter segurança máxima em nosso bucket,
para que somente nós possamos fazer upload de arquivos para ele.
Próximo para controle de versão do bucket.
Portanto, queremos desativar o controle de versão do bucket
neste momento, e veremos mais tarde como ativá-lo.
Não são necessárias etiquetas.
E para a criptografia padrão, usarei a criptografia
do lado do servidor com a chave gerenciada do
Amazon S3.
Portanto, todos os meus objetos serão criptografados,
e eu escolherei a primeira opção.
Falaremos sobre criptografia mais adiante.
E a chave de balde, eu a habilitarei.
Portanto, deixaremos, como você pode ver, todas as configurações como padrão.
A única coisa que definimos, na verdade, é o nome do balde.
Então, vou criar meu balde.
E agora ele foi criado com sucesso.
E você verá aqui na interface do usuário todos os seus buckets.
Se você tiver o diretório ativado,
verá também os compartimentos de diretório;
no momento, não tenho nenhum.
Mas seus baldes de uso geral estão aqui.
Neste momento, você deve ver um balde se tiver
acabado de criar esse curso.
Para mim, tenho
33 porque tenho usado bastante minha conta.
E isso implantará buckets para todas as regiões da AWS, não apenas aquela
em que você está agora, mas todas as regiões.
Como você pode ver, tenho a Irlanda e Londres.
Eu rolo a tela para baixo e vejo us-east-1, Frankfurt e assim por diante.
Assim, todos os seus compartimentos serão exibidos aqui,
e você poderá fazer uma pequena pesquisa.
Por exemplo, stephane-demo, e aqui
está meu bucket.
Então, vou clicar nele e dar uma olhada em seu interior.
E agora, no meu balde, eu
gostaria de começar a carregar objetos, porque
atualmente você não tem nenhum objeto.
Então, vamos clicar em upload e, em seguida, podemos adicionar arquivos.
Navegue até o seu código, vá até a pasta S3 e você encontrará
um café. arquivo jpg.
Portanto, escolha este café. arquivo jpg.
Como você pode ver, é uma imagem
jpg, com 100 kilobytes de tamanho.
E o destino é o S3 stephane demo, que é o meu
balde.
Ok, então vamos carregar esse arquivo.
Terminamos.
Assim, posso fechar isso no lado direito.
E agora de volta ao meu balde S3.
Estou vendo o café. O arquivo jpg está em meus objetos.
Assim, posso clicar nele e obter
mais detalhes sobre esse arquivo.
Portanto, agora que estamos na página do objeto, podemos
dar uma olhada em várias visões gerais.
Portanto, há várias propriedades nas quais ele foi carregado,
o tamanho, o tipo e há um URL de objeto aqui.
Vamos reproduzi-lo em instantes.
Então, como fazemos isso?
Portanto, agora queremos abrir esse
objeto e ver se podemos abri-lo.
Podemos visualizá-lo porque o carregamos
em nossos buckets do Amazon S3.
Portanto, vou clicar em abrir.
E se eu clicar em abrir, como você pode ver, poderei
ver meu café. arquivo jpg.
Então, este é o que eu carreguei
e está na Internet.
Incrível, não é?
Mas se eu voltar à minha visão geral e clicar
nessa url de objeto aqui.
Então, eu o copio, colo e insiro.
Como você pode ver, recebo uma mensagem de acesso negado.
E esse acesso negado me diz que
não posso acessar meu objeto usando o que é
chamado de URL público.
Portanto, você pode ver aqui que esse URL público não está funcionando,
mas esse URL está funcionando.
Então, qual é a diferença?
Bem, este URL aqui,
se você der uma olhada nele, o início é exatamente
o mesmo, mas o resto é um URL muito, muito complicado e longo, porque
é chamado de URL pré-assinado do S3.
Por quê?
Bem, porque esse URL contém, na verdade, uma assinatura que verifica
que sou eu quem está fazendo a solicitação e, portanto,
contém minhas credenciais.
Assim, como minhas credenciais estão codificadas nesse URL, o Amazon S3
diz: "Bem, Stephane tem
permissão para visualizar seu próprio objeto, portanto,
vou exibi-lo". Portanto, esse URL público
não funciona, mas esse URL pré-assinado
com minhas próprias credenciais funciona e,
é claro, esse URL é somente para mim.
Portanto, veremos como tornar esse objeto público mais adiante, para
que o URL público também funcione.
Então, vamos voltar ao nosso bucket, o stephane-demo-s3.
E eu tenho um objeto, mas posso criar uma pasta.
E esse nome de pasta pode ser chamado de imagens.
Então, rolamos a tela para baixo e criamos essa pasta.
Portanto, agora tenho a pasta de imagens em meu bucket.
Posso clicar nele e, dentro
dele, posso carregar novamente um arquivo.
E, desta vez, farei o upload da praia. jpg, como você pode ver,
o destino é minha pasta de imagens nos
meus buckets do S3.
Então, vamos fazer o upload disso.
Feche isso.
Como podemos ver agora, temos a praia. jpg dentro da
pasta de imagens.
E se eu subir um nível, poderemos ver a pasta aqui.
Portanto, ele se parece com
o serviço de armazenamento em nuvem que você
costumava conhecer, como o Google Drive ou o Dropbox, ou o
que você quiser.
Aqui, temos algo muito semelhante
em termos de experiência do usuário no Amazon S3.
Portanto, é claro que posso ir para
imagens e excluir essa pasta completamente.
Portanto, isso excluirá tudo o que estiver dentro da pasta.
E para excluir coisas,
basta digitar permanentemente delete nas entradas de texto,
excluir meus objetos e pronto.
Então é isso para esta palestra.
Já vimos como podemos fazer upload de objetos no Amazon S3.
Vimos como podemos abri-las de duas maneiras diferentes,
criando pastas, excluindo pastas e assim por diante.
Espero que tenham gostado
e nos veremos na próxima palestra.
