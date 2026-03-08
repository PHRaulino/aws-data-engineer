Então, agora vamos falar sobre o Amazon S3-Security.
Portanto, como usuário, você pode ter políticas de IAM
e essa política de IAM autorizará quais
chamadas de API devem ser permitidas para um usuário de IAM específico.
Você também pode ter a segurança baseada em recursos.
Portanto, isso é novo.
Podemos usar o que é chamado de políticas de bucket do S3 e há regras
para todo o bucket que podem ser
atribuídas diretamente no console do S3.
E isso permitirá, por exemplo, que um usuário específico entre
ou permita que um usuário de outra conta,
o que é chamado de cross-account,
acesse seus S3 Buckets.
Também é assim que tornaremos nossos S3 Buckets públicos,
como mostrarei em um minuto.
Em seguida, temos a Lista de Controle de Acesso a Objetos (ACL), que
é uma segurança de granulação mais fina e pode ser desativada.
E se você precisar ir para
o nível do Bucket, poderá ter a ACL de Buckets, que é muito
menos comum e também pode ser desativada.
E a maneira mais comum agora de fazer a segurança
em um Bucket do Amazon S3 é usar as políticas do Bucket.
Então, em que situação um princípio de IAM
pode acessar um objeto S3?
Bem, se as permissões do IAM permitirem ou se as políticas
de recursos permitirem e se não houver
uma negação explícita na ação, o princípio do IAM
poderá acessar o objeto S3 na chamada de
API especificada.
Então, vamos dar uma olhada nesses casos de uso em um minuto.
Por fim, outra maneira de fazer a segurança no Amazon S3 é criptografar
os objetos usando chaves de criptografia.
Então, como é de fato a política do S3 Bucket?
Porque esse é o foco do S3-Security para nós.
Portanto, elas são políticas baseadas em JSON e têm a seguinte aparência.
Portanto, trata-se de documentos JSON e é muito fácil de ler.
Portanto, a primeira coisa é que você tem
um bloco de recursos e o recurso informa à política
em quais buckets e objetos essa política se aplica.
E aqui podemos ver que isso se aplica a todos os
objetos do exemplo Bucket,
e é para isso que serve a estrela.
Em seguida, temos o efeito.
Então, Permitir ou Negar, e o que permitimos ou negamos?
Bem, nós negamos ações.
Portanto, temos um conjunto de APIs que podemos permitir
ou negar e, neste exemplo, a ação que permitimos é GetObject.
Portanto, isso permite que qualquer pessoa, graças ao princípio, apresente
a conta ou o usuário para aplicar a política, de
modo que o princípio é a estrela.
Portanto, aqui permitimos que qualquer pessoa com uma estrela use GetObject, de modo
que, para recuperar um objeto do meu exemplo de Bucket com um início, isso
significa qualquer objeto dentro dele.
Portanto, esse Bucket S3 está definindo leituras públicas em
todos os objetos dentro dos meus Buckets.
Portanto, podemos usar uma política de Bucket
S3 para conceder acesso público ao
Bucket, como a mostrada no lado direito,
ou para forçar os objetos a serem criptografados
no upload ou para conceder acesso a outra conta.
Então, vamos dar uma olhada na situação.
Portanto, aqui está uma política de balde para acesso público.
Portanto, temos um usuário, que está na Web mundial,
é um visitante do site e deseja
acessar arquivos em nossos Buckets S3.
Portanto, anexaremos uma política do S3 Bucket
que permite o acesso público.
Esse é o que você viu no slide anterior.
E quando essa política de bucket for anexada ao bucket S3, poderemos
acessar qualquer objeto dentro dele.
Isso é o que veremos no hands-on.
Mas outra maneira
de fazer isso é que, se você tiver um usuário
em sua conta, ou seja, um usuário
IAM e esse usuário quiser acessar o Amazon S3,
poderemos atribuir permissões IAM a esse usuário
por meio de uma política.
E, portanto, como a política permite o acesso
aos S3 Buckets, o usuário
pode acessar nossos S3 Buckets agora mesmo.
Se tivermos uma instância do EC2 e quisermos conceder
acesso da instância do EC2 aos buckets do S3, vimos que
os usuários do IAM não são adequados.
Em vez disso, precisamos usar as funções do IAM.
Portanto, criamos uma função de instância
do EC2 com as permissões IAM corretas
e essa instância do EC2 poderá acessar
os Buckets do Amazon S3.
Mais avançado, se
quisermos permitir o acesso entre contas, devemos
usar a política de bucket.
Portanto, temos um usuário IAM em outra conta da AWS e criamos
uma política de bucket S3 que permite
o acesso entre contas para esse usuário IAM específico e, portanto, o
usuário IAM poderá fazer chamadas de API em nossos
buckets S3.
Outras configurações de segurança
que você precisa conhecer são as configurações de Bucket
para Bloquear acesso público.
Portanto, foi isso que definimos como proprietário quando criamos os Buckets
e essas configurações foram inventadas pela AWS
como uma camada extra de segurança para evitar vazamentos de dados da empresa.
Portanto, mesmo que você defina uma política de Bucket
S3 que o torne público, se essas configurações
estiverem ativadas, o Bucket nunca será
público.
Portanto, isso é para evitar vazamentos de dados.
Portanto, se você sabe que seu Bucket nunca deve ser público,
deixe essas configurações ativadas
e você terá esse nível de segurança
contra pessoas que definiriam a política errada do S3 Bucket.
E se você souber que
nenhum dos seus Buckets S3 deve ser público, poderá
definir isso no nível da conta.
Muito bem, então é isso para o S3-Security.
Agora vamos praticar com as mãos.
