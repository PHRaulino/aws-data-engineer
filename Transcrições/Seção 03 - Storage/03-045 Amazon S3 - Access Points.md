Então, agora vamos falar sobre os pontos de acesso S3.
de um bucket S3 que tem muitos dados.
Temos dados financeiros, temos dados
de vendas e temos diferentes
usuários ou grupos que desejam acessar seus dados.
Poderíamos criar uma política de bucket S3 muito complicada e
fazê-la crescer com o tempo.
Quanto mais usuários e mais dados você
tiver, mais incontrolável isso poderá se tornar.
Então, qual é a solução?
Bem, podemos criar o que chamamos de pontos de acesso S3.
Assim, podemos,
por exemplo, criar um ponto de acesso financeiro
que será conectado aos dados financeiros.
Como ele está conectado aos dados financeiros?
Bem, vamos definir uma política de ponto
de acesso e essa política se parece com uma política de bucket
do S3 e concederá acesso de leitura e gravação
ao prefixo financeiro.
Em seguida, podemos definir um ponto de acesso de vendas.
E, novamente, isso será conectado aos dados de vendas graças
a uma política de ponto de acesso, uma
política diferente anexada a esse ponto de acesso,
que concederá acesso de leitura e gravação ao prefixo
de vendas.
Como você pode ver, agora tenho duas políticas
e, se eu quiser ter um ponto de acesso de análise, bem, podemos
criá-lo de modo que ele aponte para finanças e vendas, mas com
acesso somente leitura.
Portanto, vamos criar nossa própria política de somente leitura
no ponto de acesso do Analytics.
Portanto, você pode ver aqui que transferimos o gerenciamento de segurança
da política do bucket S3 para os pontos de acesso, e cada
ponto de acesso terá sua própria segurança.
Portanto, com as permissões de IAM adequadas, nossos
usuários podem acessar os pontos de acesso financeiro
e se conectar somente à parte financeira do nosso bucket.
Os usuários de vendas também só podem acessar as vendas
e o grupo de análise pode acessar finanças e
vendas ao mesmo tempo.
Portanto, ao usar pontos de acesso, definimos diferentes
maneiras de acessar nosso bucket S3.
E o resultado disso é que temos uma maneira
muito simples de gerenciar a segurança.
Temos políticas anexadas a cada ponto de acesso
e também temos uma política de bucket muito simples no Amazon S3.
Portanto, podemos realmente dimensionar o acesso aos nossos buckets S3.
Portanto, para resumir os pontos de acesso, simplifique os gerenciamentos
de segurança para os buckets S3, e cada ponto de acesso terá seu próprio
nome DNS.
É assim que você se conecta ao ponto de acesso.
Você pode optar por conectá-lo à Internet como
uma origem ou uma VPC para tráfego privado.
E, em seguida, você anexa novamente uma política de ponto de
acesso, que é muito semelhante à política de balde.
E isso permite que você gerencie a segurança em escala.
Com relação à origem VPC dos pontos de acesso S3,
podemos defini-los como de acesso privado.
Assim, por exemplo, uma instância
EC2 em um acesso VPC diz que, sem passar pela Internet, nosso
bucket S3 passa pelo ponto de acesso VPC por meio de
uma origem VPC.
Portanto, para obter acesso a essa origem VPC, devemos
criar o que chamamos de endpoint VPC para acessar
o ponto de acesso.
Portanto, é algo em nossa VPC que nos permitirá conectar
de forma privada ao ponto de acesso por meio de nossa origem VPC.
E o endpoint da VPC tem uma política, e essa
política deve permitir o acesso aos
buckets de destino e aos pontos de acesso.
Portanto, a política de endpoint da VPC permitirá que nossa
instância do EC2 se conecte à VPC, aos pontos de acesso
no Amazon S3 e aos buckets do S3.
Portanto, nesse caso, temos o endpoint VPC para segurança.
Também temos segurança para a política
de ponto de acesso e segurança no nível do bucket S3.
Tudo bem. Isso é tudo para os pontos de acesso.
Espero que tenham gostado e nos veremos na próxima palestra.
