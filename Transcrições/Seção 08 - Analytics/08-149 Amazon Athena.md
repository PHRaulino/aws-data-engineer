Trata-se de um mecanismo de consulta interativa sem servidor para dados do S3,
o que é muito legal.
Você pode pegar um lago de dados potencialmente enorme no
S3 e simplesmente colocar
o Athena em cima dele e consultá-lo
como se fosse um banco de dados SQL.
O que é Athena?
Tecnicamente, trata-se novamente de
uma descrição, um serviço de consulta interativa para o S3.
Então, novamente, é basicamente uma interface
SQL para seus dados no S3.
Não há necessidade de carregar esses
dados em algum banco de dados intermediário.
Os dados simplesmente permanecem no
S3 e o Athena sabe como interpretá-los e consultá-los
como se fossem um banco de dados real.
Na parte interna, ele usa o Presto, mas
você não precisa saber disso.
Foi mais ou menos assim que eles começaram a construir o Athena.
No entanto, ele evoluiu bastante desde
então, de modo que suas raízes podem
ter sido no Presto, mas atualmente ele é mais próprio.
A grande vantagem do Athena,
no entanto, é que ele é totalmente sem servidor,
portanto, você não precisa pensar nos servidores subjacentes, na
capacidade ou em algo do gênero.
Basta acessar o Athena, apontá-lo para seus dados no S3 e
começar a escrever consultas.
Bem, você pode fazer mais do que
isso, mas pode fazer apenas isso.
Isso é tudo o que há para fazer.
Basta acessar a interface do usuário, o console do Athena,
e ir para a cidade.
Você não precisa pensar
em configurar toda a capacidade subjacente.
Tudo isso é abstraído para você.
Ele suporta muitos formatos de dados diferentes,
de modo que seus dados no S3 podem ser praticamente qualquer coisa que
você possa imaginar, seja um valor separado por vírgula
ou um valor separado por tabulação.
Ambos são legítimos.
Portanto, qualquer dado legível por humanos pode ser colocado
no Athena e ele pode compreendê-lo e consultá-lo.
O formato JSON também é compatível.
O formato colunar ORC também é compatível.
A vantagem do ORC e do Parquet
é que ambos são formatos divisíveis,
o que pode ser útil para melhorar o desempenho e segmentar
os dados de forma que faça sentido
para suas consultas.
Avro, também pode ser dividido.
E, no que diz respeito à compactação,
você pode armazenar seus dados em compactação
Snappy, Zlib, LZO ou Gzip.
Agora, há algumas conclusões que você
deve ter em mente para o exame.
Lembre-se de que o ORC e o Parquet
são formatos colunares e divisíveis.
A Avro só pode ser dividida.
CSV, TSV e JSON são todos formatos legíveis por humanos, certo?
Portanto, CSV, TSV, JSON, você pode abrir esse arquivo em
um editor de texto e entendê-lo.
ORC, Parquet, Avro, nem tanto.
O Avro poderá ser dividido, portanto,
você poderá processar os dados do Avro em paralelo,
pois o Athena pode dividi-los e processá-los em paralelo em diferentes
partes, certo?
Além disso, o ORC e o Parquet são formatos de coluna, o que pode
acelerar as consultas que são
específicas apenas para determinadas colunas.
E praticamente qualquer compressão que você
possa imaginar também é suportada.
Portanto, para fins de exame, essas
são as coisas que você deve lembrar.
Os dados em si podem ser não estruturados, semiestruturados
ou estruturados.
Athena não se importa.
Portanto, qualquer que seja o nível de esquema que você tenha,
ele pode tirar proveito dele ou pode inferir um novo esquema apenas
examinando os dados ou pegando
um que você tenha fornecido a ele.
Alguns exemplos de uso dados aqui pela Amazon
incluem a consulta ad-hoc de registros da Web.
Portanto, o Athena é dado como um exemplo melhor de como
lidar com a consulta de dados de registro da Web no S3, e eles
preferem que você o use em vez
do Elasticsearch, por exemplo.
Você também pode usá-lo para consultar dados de preparação
antes de carregá-los no Redshift.
Então, talvez você tenha um monte de dados sendo despejados no
S3 e queira transformá-los e carregá-los
em um grande data warehouse do Redshift, mas talvez
você queira poder brincar com esses dados,
investigá-los e ver como eles são antes.
O Athena pode ser uma boa maneira de obter
uma visão mais ampla da aparência
desses dados antes de colocá-los em um data warehouse.
Também é útil para examinar outros logs além
dos logs da Web no S3, incluindo logs
de trilha de nuvem, logs de frente de nuvem, logs de VPC, logs de balanceador de
carga elástica.
O que quer que você tenha, se estiver no S3, o Athena poderá consultá-lo.
Ele também oferece integração com ferramentas como os notebooks
Jupyter, Zeppelin e RStudio, porque
você pode tratá-lo como um banco de dados.
Ele tem interfaces ODBC e JDBC, de modo que você pode tratar o Athena como qualquer outro banco
de dados relacional com o qual você
possa interagir ou se integrar.
Isso também inclui o QuickSight.
Você também pode
integrar a ferramenta de visualização QuickSight da Amazon ao Athena
para usá-la como uma espécie de cola,
bem, cola é uma má escolha de palavra, pois estamos
usando o serviço Glue para isso, mas a coisa que
conecta seus dados não estruturados no S3 a uma ferramenta de visualização
ou análise mais estruturada, como o QuickSight.
