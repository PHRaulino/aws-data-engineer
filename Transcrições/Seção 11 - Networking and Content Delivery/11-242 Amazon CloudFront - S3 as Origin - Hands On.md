Então, vamos praticar o uso do
CloudFront,
mas primeiro precisamos criar um bucket S3
para manter nossos arquivos para nossa
distribuição.
Então, vamos criar um bucket, que
chamarei de demo-CloudFront-Stephan-v4, e
ele rolará
e clicará em Create Bucket.
Ok, então meu bucket foi criado e
vou fazer upload de alguns arquivos nele.
Então, deixe-me adicionar arquivos e
escolherei meus três arquivos:
beach, coffee e index.html.
Então, vamos fazer o upload deles.
E agora que eles foram carregados, se eu
entrar em meu balde, poderemos ver todos
eles.
E, como lembrete, se eu acessar o
index.html, terei duas maneiras de
abri-lo.
A primeira é usar o URL do objeto.
Mas se eu tentar fazer isso, recebo uma
mensagem
de acesso negado porque meu objeto não é
público.
E se eu clicar em abrir
aqui, isso gera uma pré-assinatura.
Portanto, vamos permitir pop-ups.
Isso gera um URL pré-assinado para meus
objetos
S3, o que me permite acessar o objeto.
Então você vê "I love coffee" e "hello
world", mas eu ainda não vejo a imagem
porque a imagem em si não é pública.
Então, vamos ver como podemos usar o
CloudFront
para tornar esses arquivos acessíveis sem
torná-los públicos.
Então, vamos abrir o console do
CloudFront.
Primeiro, tenho uma janela pop-up sobre
preços, então vou clicar em
não mostrá-la novamente e fechá-la.
Então, vamos criar uma distribuição do
CloudFront.
Portanto, a primeira coisa a fazer é
selecionar um plano.
Portanto, agora há vários planos para o
CloudFront e,
como você pode ver, eles têm recursos
diferentes.
Mas se dermos uma olhada, o
plano gratuito será suficiente para nós.
Portanto, temos solicitações e permissão
suficientes por
mês, vamos ter proteção de DNS sempre
ativa, bloqueio de tráfego geográfico e
CDN
global, DNS e certificados TL gratuitos.
Portanto, tudo isso é suficiente para
o que precisamos para o CloudFront.
Mas se você precisar de algo como, por
exemplo,
armazenamento de valor-chave de borda ou
proteção avançada
contra DDoS ou SLA de tempo de atividade
ou proteção para WordPress, esses tipos de
coisas,
então um desses planos será melhor para
você.
E, por fim, você tem a opção pay as you
go,
que consiste em pagar com base no tráfego
que você usa.
E então você terá que
pagar mais por alguns recursos.
Mas, para manter as coisas simples, vamos
manter como livre,
pois isso será suficiente para o nosso
caso de uso.
Portanto, esse será chamado de demo new
CloudFront.
E aqui temos apenas a opção de
usar um único site ou aplicativo.
Não precisamos ter um domínio, mas podemos
adicionar um
domínio e provisionar um certificado TLS
para nós.
Vamos clicar em next.
E agora temos que dizer qual é o tipo
de origem? Portanto, como você pode ver
agora,
temos Amazon S3, balanceador de carga
elástico, gateway
de API, pacote de mídia elementar ou
outro.
E a origem VPC, se você quiser se conectar
diretamente a uma instância privada do EC2
ou
a um aplicativo de balanceador implantado
de forma
privada, só estará disponível no plano de
negócios.
Mas ainda é uma opção do que o CloudFront
pode fazer.
Portanto, usaremos o Amazon S3.
Em seguida, temos que navegar pelo Amazon
S3.
E usaremos uma demonstração do CloudFront
stephane v4.
Está bem.
Em seguida, vamos permitir o acesso
do bucket S3 privado ao CloudFront.
Sim, e usaremos as configurações de origem
recomendadas e as configurações de cache
recomendadas
para atender ao conteúdo do S3.
Portanto, agora a configuração é bastante
simples.
Se quisermos ter segurança, podemos ativar
o firewall
de aplicativo da Web, mas isso não
é algo de que precisamos no momento.
E se você quiser ter proteção contra a
camada
7, novamente, isso está disponível com o
plano empresarial.
Portanto, no momento, não quero nada.
Vou clicar em - Certifique-se de
que temos o plano gratuito.
Sim, isso é bom.
A interface do usuário é um pouco
contraintuitiva
nesse caso, mas vamos voltar ao assunto.
Portanto, não precisamos de nenhum
firewall de aplicativo da Web.
Clicamos em next e podemos revisar tudo.
Portanto, sim, estamos no plano gratuito
e vamos criar nossa distribuição.
Pronto, minha distribuição já foi criada.
Agora, se eu entrar no S3 e examinar as
permissões e a política do meu bucket,
posso ver
que agora, na minha política de bucket,
tenho uma
política de bucket que permite o acesso ao
meu
bucket a partir da nossa distribuição do
CloudFront.
Esses são dois porque eu tinha dois, um é
um teste
e o outro é o que acabei de criar para
você.
Como podemos ver, isso permite que nossa
distribuição do
CloudFront acesse de forma privada nossos
buckets S3.
Portanto, isso foi inserido como uma
política de bucket
pelo serviço de plataforma quando estava
sendo implantado.
Portanto, minha distribuição está pronta e
posso
clicar no nome do domínio, abrir
uma nova guia e pressionar Enter.
Agora vou receber uma mensagem de acesso
negado, mas está tudo bem.
Isso ocorre porque preciso entrar em um
caminho específico.
Portanto, /coffee.jpg.
Como você pode ver, a imagem do meu café
está sendo carregada.
Ou /beach.jpeg.
E, novamente, minha imagem da praia está
carregando.
E agora, se eu for para index.html,
terei minha imagem completa com "I love
coffee" e "hello world" e esta imagem.
Portanto, mesmo que todos os objetos do
meu bucket
sejam privados, agora, como temos essa
política de bucket
que permite o acesso pelo CloudFront,
posso ver tudo
o que preciso ver por meio do CloudFront.
Mas agora o benefício adicional é que, se
eu voltar para beach.jpeg, a imagem será
armazenada
em cache e o carregamento será quase
instantâneo.
Então, de volta para cá.
Novamente, o carregamento é muito, muito
rápido.
E esse é o benefício do CloudFront.
Então é isso.
Criamos uma distribuição do CloudFront no
plano
gratuito, configuramos o S3 como uma
origem
e vimos a política do bucket.
Espero que tenham gostado e
nos veremos na próxima palestra.
