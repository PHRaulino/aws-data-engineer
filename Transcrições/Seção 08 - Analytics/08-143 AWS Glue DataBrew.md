Vamos falar sobre o Glue DataBrew.
Isso é definitivamente algo que você precisa
porque essa é uma ferramenta visual de preparação de dados.
Portanto, é outra interface de usuário que você
pode usar apenas para transformar dados, fazendo o T do seu ETL.
Portanto, muito, muito, muito relevante para este exame.
É uma interface de usuário para pré-processamento de grandes conjuntos de dados.
Esses conjuntos de dados podem vir do S3, de um data warehouse ou de qualquer
banco de dados que você desejar.
A saída, no entanto, irá para o S3 depois
de ser transformada pelo DataBrew.
E há mais de 250 transformações prontas que você
pode aplicar visualmente a esses dados.
Assim, você pode simplesmente arrastar e soltar essas coisas
no DataBrew e fazer com que
ele transforme automaticamente seus dados de praticamente
qualquer maneira que você possa imaginar.
E não vou analisar todos os 250.
Se você quiser consultar a documentação
no site da AWS e, pelo menos, dar uma olhada, não custa nada.
É bom saber quais são os recursos,
mas a versão resumida é que praticamente qualquer
coisa que você possa imaginar provavelmente está lá.
Você pode criar essas receitas de transformações
que podem ser salvas como trabalhos em um projeto maior.
Portanto, se você tiver várias transformações que
deseja aplicar aos seus dados, poderá
criar uma receita dessas transformações, salvá-la
e aplicá-la a diferentes lugares,
projetos e conjuntos de dados.
Essas receitas são compostas de ações de receita.
E se você acessar a documentação das transformações, verá
as definições dessas ações de receita.
Como exemplo, aqui à direita, esta é uma
ação de receita chamada NEST TO MAP.
E isso é usado para pegar colunas selecionadas e convertê-las
em pares de valores-chave.
Portanto, em vez de colunas individuais,
isso pode ser convertido em um documento JSON que tenha
esses mapeamentos de valores-chave entre
essas colunas e seus valores.
Portanto, não sei por que você quer fazer isso,
mas você pode fazer isso.
E você também pode, opcionalmente, remover as colunas de origem que
você combinou nesse mapa, bem como parte dele.
Portanto, é isso que está acontecendo aqui nos parâmetros.
Estamos especificando quais colunas de origem queremos aninhar.
Então, vamos pegar as colunas de idade, peso
em quilogramas e altura em centímetros.
Vamos colocá-las em uma nova coluna
única chamada columnName, onde serão armazenadas
como esse mapa baseado em
JSON que dirá, por exemplo, que a idade é igual a 53, o peso em quilogramas
é igual a 100, a altura em centímetros é igual a 500, seja o que for,
certo?
Você pode perceber que eu não lido com o sistema métrico,
pois tenho certeza de que esses números não fazem sentido.
E também dizemos removeSourceColumns.
Portanto, as colunas originais de idade, peso e altura
serão excluídas como parte da transformação do Nest to Map.
Você também pode definir regras de qualidade
de dados, como parte do DataBrew, para garantir que seus dados
façam sentido à medida que você avança.
E você também pode criar conjuntos
de dados com SQL personalizado do Redshift e do Snowflake
como parte do DataBrew.
Do ponto de vista da segurança, o DataBrew se integra
ao KMS usando apenas as chaves mestras do cliente.
É claro que ele usa SSL em trânsito, e você pode usar
o IAM para restringir quem pode fazer o quê, como na
maioria dos serviços.
Além disso, como acontece com a maioria
dos serviços, ele se integra ao CloudWatch e ao CloudTrail
para alarmes, governança e todas essas coisas boas.
