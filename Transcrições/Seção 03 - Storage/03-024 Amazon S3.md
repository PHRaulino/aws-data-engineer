Portanto, esta seção é muito
importante porque o Amazon S3 é um dos principais blocos de construção do AWS e a
forma como é anunciado é
que ele é um armazenamento de escala infinita.
De fato, grande parte
da Web depende do Amazon S3.
Por exemplo, muitos sites usam o Amazon S3 como backbone
e muitos serviços da AWS também usarão o Amazon S3 para
integrações.
Portanto, nesta seção, faremos uma abordagem passo a passo
do Amazon S3 para conhecer os principais recursos.
Portanto, há muitos casos de uso
para o Amazon S3, pois sua essência é o armazenamento S.
Portanto, imagine que o S3 seja usado para backup e armazenamento.
Pode ser para seus arquivos, pode
ser para seus discos e assim por diante.
Para fins de recuperação de desastres.
Por exemplo, você moverá seus dados para outra região.
Caso uma região fique inoperante,
seus dados serão armazenados em outro local.
É para fins de arquivamento.
Assim, você pode arquivar arquivos no Amazon
S3 e recuperá-los posteriormente
por um preço muito, muito mais barato.
Para armazenamento em nuvem híbrida.
Portanto, se você tiver armazenamento no local,
mas não quiser expandi-lo para a nuvem,
poderá usar o Amazon S3 para isso.
Para hospedar aplicativos, para hospedar mídia, como arquivos de vídeo,
imagens e assim por diante.
Ter um lago de dados, para armazenar muitos
dados e realizar análises de big data, para fornecer
atualizações de software, para hospedar
sites estáticos e assim por diante.
E dois casos de uso são que a Nasdaq armazena sete
anos de dados no serviço de compartilhamento S3 Glacier,
que é como o serviço de arquivamento do Amazon S3.
E a Sysco executa análises em seus dados
e obtém insights comerciais do Amazon S3.
Portanto, o Amazon S3 armazena arquivos em buckets.
E os buckets podem ser vistos como diretórios de nível superior.
E, na verdade, os arquivos
nesses buckets do S3 são chamados de objetos.
E esses buckets são criados em sua conta e devem ter
um nome globalmente exclusivo.
Isso significa que o nome deve ser
exclusivo em todas as regiões em que você o tem
em suas contas, mas também em todas as contas que existem na AWS.
Portanto, essa é a única
coisa que deve ser globalmente exclusiva na AWS.
E os compartimentos são definidos no nível da região.
Portanto, mesmo que o nome do bucket seja
exclusivo em todas as regiões e em todas
as contas, os buckets devem ser definidos em uma região específica da AWS.
Portanto, o three parece um serviço global,
mas os buckets são, na verdade, criados em uma
região, e esse é um erro comum para iniciantes.
Portanto, há uma convenção de nomenclatura para os buckets do S3.
Você não se lembra disso, mas é bom saber.
Portanto, os nomes dos baldes não devem ter letras maiúsculas nem sublinhados.
Eles devem ter entre três e 63 caracteres.
Eles não devem ser um IP.
Eles devem começar com um número minúsculo ou uma letra minúscula.
Além disso, há algumas restrições de prefixo.
Portanto, contanto que você use letras, números e hífens,
não há problema.
Agora, vamos falar sobre objetos.
Portanto, esses objetos são arquivos
e têm o que chamamos de chave.
E uma chave de objeto do Amazon S3 é o caminho completo do seu arquivo.
Portanto, se você olhar para o meu bucket, este
é o diretório de nível superior.
Então, a chave do meu arquivo em TXT é meu arquivo ponto TXT.
Mas, caso você queira aninhá-lo no que chamamos de pastas,
a chave será o caminho completo.
Portanto, minha pasta um barra outra pasta barra meu arquivo ponto TXT.
Portanto, a chave é composta
de um prefixo e, em seguida, de um nome de objeto.
Assim, podemos, por exemplo, decompor o caminho anterior
no prefixo, que é minha pasta um e outra pasta, e o nome
do objeto, que é meu arquivo ponto TXT.
Portanto, o Amazon S3 não tem um conceito de diretórios em si, embora,
ao olhar o console, a interface do usuário, você
pense o contrário
e realmente crie diretórios.
Mas tudo e qualquer coisa no Amazon S3 é, na verdade, uma chave.
E as chaves são apenas nomes muito, muito longos
que contêm barras, e as chaves são compostas
por um prefixo e um nome de objeto.
Então, o que são os objetos?
Bem, seus valores são o conteúdo do corpo.
Assim, você pode fazer upload de
um arquivo, pode fazer upload do que quiser no histórico da Amazon.
Portanto, o tamanho máximo do objeto é de cinco terabytes.
Portanto, são 5.000 gigabytes.
E se você fizer upload de um arquivo muito grande e se esse arquivo
for maior que cinco gigabytes, ou seja, um arquivo grande,
tudo bem, então você deve usar o upload de várias partes para
fazer upload desse arquivo em várias partes.
Portanto, se você tiver um arquivo de cinco
terabytes, deverá fazer upload de pelo menos 1.000 partes de cinco gigabytes.
Agora, o objeto também pode ter metadados,
sua lista de pares de chave e valor, e isso pode ser definido pelo
sistema ou pelo usuário para indicar alguns elementos sobre o arquivo,
alguns metadados.
Suas tags, por exemplo, seus pares de chave e valor
Unicode de até 10, são muito
úteis para segurança e ciclos de vida e, às
vezes, o objeto terá um ID de versão se você tiver ativado
o controle de versão.
Então é isso para uma introdução ao Amazon S3.
Tenho certeza de que você está curioso para
saber como isso funciona, então vamos entrar no console para começar.
