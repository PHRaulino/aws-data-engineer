Então, vamos criar uma
política de bucket para que possamos
acessar esse arquivo de café a partir do
URL público.
E a primeira coisa que temos que fazer
é permitir o acesso público a partir da
configuração do balde, porque agora tudo
está bloqueado.
Então, editamos isso e desmarcamos a opção
e, portanto, permitiremos o acesso
público.
Mas, novamente, isso é algo que você
desativaria
somente, e somente se, você sabe que
deseja definir uma política de bucket
público.
Portanto, essa é uma ação perigosa.
Por isso, dizemos que sim, porque, é
claro, se você colocar
dados reais da sua empresa em um bucket S3
e torná-los
públicos, haverá vazamentos de dados e
isso nunca será bom.
Portanto, agora, na visão geral das
permissões,
o acesso aos objetos pode ser público.
Portanto, esse é o primeiro passo.
Em seguida, rolamos a tela para baixo e
damos uma olhada na política do Bucket.
Portanto, atualmente não temos nenhum e
queremos criar
um para tornar todo o nosso balde público.
Portanto, a primeira coisa que você pode
fazer é examinar o exemplo de políticas,
que é a documentação, e ele mostrará
vários casos de uso no lado
direito que mostrarão qual é a
política de bucket apropriada e
correspondente.
Mas, para nós, usaremos o gerador de
políticas.
Aqui está o AWS Policy Generator, e
vamos criar uma política de bucket S3.
Portanto, vamos selecionar o tipo certo.
Permitiremos e, em seguida, o principal
será
uma estrela, porque queremos permitir que
qualquer pessoa no serviço Amazon S3
execute e, como leremos objetos em
nosso bucket, queremos executar um
getObject.
Então, aqui está.
Queremos permitir getObjects.
E o Amazon Resource Name deve ser o nome
do
bucket com uma barra e depois com uma
estrela.
Então, vamos dar uma olhada primeiro.
Então, de volta aos nossos buckets S3,
temos o bucket
arn aqui, o nome do recurso da Amazon
aqui.
Então, nós o copiamos e colamos no Amazon
Resource Name, e isso ainda não acabou.
Adicionamos uma barra e depois uma
estrela.
E a razão pela qual fazemos isso
é que essa ação, a ação getObject
aqui, aplica-se a objetos em seus buckets
e, portanto, os objetos em seu
bucket estão após uma barra e
há estrelas para representar esses
objetos.
Então, vamos adicionar essas declarações
e gerar essa política.
E essa política é o que copiamos aqui,
e essa é uma política pública de S3.
Isso significa que getObjects é permitido
a
qualquer pessoa em qualquer objeto desse
bucket.
Muito bem, isso é bom.
Então, vamos salvar essas alterações.
E há um espaço aqui, portanto, vamos
removê-lo.
Perfeito.
Salve essas alterações.
Isso funciona.
Assim, podemos ver que nossa política
de balde foi aplicada corretamente.
Então, agora, vamos acessar nosso objeto,
coffee.jpg, e
vamos encontrar o URL do objeto, bem aqui.
Nós o copiamos e o inserimos.
E, como você pode ver agora, minha imagem
do
café está totalmente visível e é pública,
assim como
qualquer outro objeto em meus buckets do
Amazon S3.
Então é isso para esta palestra.
Vimos as políticas de balde, vimos o
gerador de
políticas e vimos que agora nossa imagem é
pública.
Espero que tenham gostado e
nos veremos na próxima palestra.
