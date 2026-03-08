sobre como colocar dados
em suas tabelas Redshift
e também como retirá-los de forma eficiente.
Portanto, seu comando para obter dados em uma tabela do
Redshift é o comando COPY.
Essa será a maneira mais eficiente
de carregar sua tabela do Redshift.
Você pode usar o comando
COPY para ler vários arquivos de
dados ou vários fluxos de dados simultaneamente,
e isso pode ser feito no Amazon S3,
no Elastic MapReduce, no DynamoDB ou em qualquer
host remoto usando o protocolo SSH.
Agora, você precisará
de controle de acesso baseado em função ou em chave para autenticar
as coisas lá, mas depois de ter toda a segurança definida,
é bastante simples.
Se você estiver importando do S3, será
necessário um arquivo de manifesto, que é apenas
um arquivo formatado em JSON que lista todos
os arquivos de dados que você deseja carregar.
E também, obviamente, uma
função IAM para lhe dar acesso a esse bucket S3 do Redshift.
Se você quiser retirar dados do Redshift,
o comando UNLOAD é a maneira de fazer isso.
Portanto, essa será apenas uma maneira
rápida de descarregar dados de uma tabela de banco de
dados para um conjunto de arquivos em um bucket S3.
Além disso, é preciso pensar no roteamento VPC aprimorado,
o que forçará todo o tráfego de cópia e descarga entre
o cluster e os repositórios por meio
do Amazon VPC.
Se você não configurar isso, todo
o seu tráfego será roteado pela Internet, portanto,
certifique-se de que a VPC esteja corretamente
instalada e configurada, ou a cópia ou o descarregamento
falhará.
Você precisa garantir que os pontos de extremidade
da VPC, o gateway NAT e o gateway da Internet estejam configurados
corretamente para que tudo isso aconteça dentro da VPC,
caso queira evitar o roteamento desses dados pela
Internet.
Portanto, outro ponto importante que o exame
pode esperar que você saiba.
Há alguns recursos mais recentes em 2023,
portanto, eu não esperaria
ver isso no exame até 2024 ou mais, mas se você
estiver observando em 2024 ou mais, pode ser importante
saber isso.
Um deles é a cópia automática do Amazon S3, que simplesmente
monitora um bucket do S3 e, à medida que novos dados
são vistos nesse bucket, ele os copia
automaticamente para o cluster do Redshift.
Portanto, essa é uma maneira de simplificar ainda mais a
importação de dados do S3. Ele pode simplesmente
ficar lá procurando novos dados o tempo todo e copiá-los
automaticamente para o Redshift para você.
Portanto, é muito mais fácil, não é mais necessário
ficar sentado e executar os comandos COPY manualmente.
Há também algo chamado
integração zero-ETL do Amazon Aurora e, com o mesmo espírito
da cópia automática do S3, que fica por perto
e replica automaticamente os dados de um banco de dados
Aurora para o Redshift o tempo todo.
Portanto, se você tiver algum banco de dados relacional Aurora
e quiser replicar esses dados nas tabelas do Redshift,
essa é uma maneira muito fácil de fazer isso
e continuar fazendo isso automaticamente.
Agora também há algo
chamado Redshift Streaming Ingestion,
que procurará novos
dados em um Kinesis Data Stream ou MSK para seu cluster
Kafka gerenciado.
Um pouco mais de profundidade no
comando COPY, o exame parece estar se concentrando cada vez mais
nisso, portanto, lembre-se de que você deseja
usar o COPY para carregar grandes quantidades de dados de fora do
Redshift em uma tabela do Redshift em seu cluster do Redshift.
Se você vir uma pergunta sobre como
carregar dados de forma eficiente no Redshift a partir de fora?
É provável que a resposta seja o comando COPY.
Agora, se seus dados já estiverem no Redshift em alguma
outra tabela, você não precisará usar a cópia.
A cópia é para dados externos que estão sendo importados
para o cluster do Redshift.
Se os seus dados já estiverem em
outra tabela no próprio Redshift,
você deve usar a instrução INSERT INTO SELECT ou CREATE
TABLE AS para criar uma tabela que seja apenas uma visualização
da outra tabela à qual você pode fazer referência.
Portanto, lembre-se de que CREATE TABLE AS é o que você
usará para fazer referência a dados que já estão no Redshift
em alguma outra tabela.
E se estiver fora do Redshift,
você deve usar o comando COPY.
Alguns recursos interessantes do comando COPY:
ele pode realmente descriptografar dados à medida que são carregados do S3.
Portanto, se seus dados do S3 estiverem criptografados, o COPY
poderá descriptografá-los à medida que forem carregados.
E ele pode fazer isso muito rapidamente
porque tem um recurso de SSL acelerado por hardware para manter
essa descriptografia o mais rápido possível.
Ele também pode acelerar o processo comprimindo os
dados à medida que são enviados.
Portanto, ele oferece suporte à compactação Gzip, lzop e bzip2 para acelerar
ainda mais essas transferências de dados quando
você estiver usando um comando COPY.
Outro recurso interessante do comando
COPY é a compactação automática.
Essa é uma opção que analisará os dados que estão
sendo carregados e descobrirá automaticamente
o esquema de compactação ideal para armazená-los.
Portanto, se você tiver dados que podem ser compactados muito bem, a compactação automática
poderá descobrir: como posso armazenar
esses dados de forma eficiente?
Isso é usado para otimizar o uso do
armazenamento real em seu cluster.
Há um caso especial que a documentação menciona
e não me surpreenderia se ele aparecesse no exame.
Se você tiver uma tabela
estreita, ou seja,
uma tabela com muitas linhas, mas muito poucas colunas,
é melhor carregá-la com uma única transação COPY,
se possível.
O problema é que, se você tiver várias transações COPY,
há várias colunas de metadados ocultas que aparecem e essas
colunas ocultas, para manter o controle
de onde as coisas pararam, consomem muito espaço.
Portanto, se você for carregar uma tabela
que tenha muitas linhas, mas poucas colunas,
tente fazer isso em um único comando COPY.
Não divida isso em vários comandos COPY, certo?
Também é importante lembrar
que o COPY foi projetado para paralelizar e fazer as coisas da forma
mais eficiente possível, portanto, se
for possível fazer as coisas em um único comando COPY, por que não?
Isso sempre funcionará bem.
É realmente surpreendente o nível de profundidade
que o exame espera de você sobre esse assunto.
Então, vamos falar sobre um caso muito específico aqui.
Digamos que você queira copiar um instantâneo do Redshift automaticamente
para outra região.
Portanto, você tem uma replicação
entre regiões de seus instantâneos para fins de backup.
Então, digamos que você tenha um cluster Redshift criptografado por
KMS e um instantâneo desse cluster
sendo salvo em alguma região do S3.
Agora você deseja copiar esse instantâneo para outra região
para obter um backup ainda melhor.
A maneira de fazer isso é a seguinte: na região de
destino do AWS, você cria uma chave
KMS, se ainda não tiver uma, e configura uma concessão
de cópia de instantâneo, especificando um nome
exclusivo para essa concessão de cópia de instantâneo
na região de destino.
Como parte da configuração dessa concessão
de cópia, você especifica a ID da chave KMS para a qual a está criando.
Em seguida, na região do AWS de origem, você
habilitará a cópia de instantâneos para
a concessão de cópia que acabou de criar.
Portanto, ao usar uma concessão de cópia configurada com uma chave
KMS, você pode copiar com segurança instantâneos criptografados por KMS
do seu cluster Redshift para outra região.
Outra curiosidade sobre conectividade é o DBLINK.
E o DBLINK é uma extensão que permite
que você conecte o cluster do Redshift a uma instância do PostgreSQL,
que pode ser hospedada usando o serviço RDS da Amazon.
Em um nível elevado, talvez você queira
fazer isso para obter o melhor dos dois
mundos entre o armazenamento em colunas do Redshift
e o armazenamento baseado em linhas do Postgres.
Ou você pode estar usando-o como uma forma de copiar e sincronizar
dados entre uma instância do PostgreSQL e o Redshift.
Portanto, se você quiser uma maneira muito eficiente de
copiar dados e manter os dados sincronizados entre o Postgres
e o Redshift, a extensão DBLINK é uma forma de fazer isso.
O funcionamento é o seguinte:
basicamente, você inicia um cluster do Redshift
e também inicia uma instância do PostgreSQL, na mesma
zona de disponibilidade, veja bem.
Em seguida, você configuraria o grupo de segurança
VPC do cluster do Amazon Redshift
para permitir uma conexão de
entrada do endpoint RDS PostgreSQL.
Em seguida, você se conectaria à instância do PostgreSQL
do RDS e executaria o código SQL que
você vê aqui, para estabelecer essa conexão
DBLINK entre a instância do PostgreSQL e o Amazon Redshift.
Portanto, lembre-se de que o DBLINK existe
para conectar o Redshift ao PostgreSQL e obter
o melhor dos dois mundos ou talvez para
copiar e sincronizar dados entre os dois
com mais eficiência.
