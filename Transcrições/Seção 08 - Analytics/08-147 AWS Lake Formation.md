Um recurso relativamente novo foi anunciado em 2018 e realmente passou por muitos refinamentos em 2020, e só agora
estamos começando a vê-lo aparecer no exame.
A formação do lago foi criada com base no glue e foi concebida como um sistema para facilitar a configuração
de um lago de dados seguro.
Seu slogan é que ele facilita a configuração de um lago de dados seguro em poucos dias.
Hum, o que eu acho que é bem rápido.
O que ele gerencia para você é o carregamento de dados de uma fonte externa e o monitoramento
desses fluxos de dados, permitindo que você se conecte às suas fontes de dados existentes, estejam elas no S3 ou
em algum banco de dados local.
Ele pode configurar partições para você.
Ele pode ajudá-lo a gerenciar a criptografia e as chaves relacionadas a ela.
E ele pode permitir que você configure as transformações associadas a esses dados desde o início.
Novamente, ele foi desenvolvido com base no glue, portanto, praticamente tudo o que o glue, o ETL ou qualquer um dos recursos do glue
pode fazer está disponível para você.
Se a faísca pode fazer isso, então a Lake Formation também pode.
Ele está apenas usando a cola sob o capô para aplicar essas transformações, e isso inclui transformá-lo em
um novo formato, como um formato colunar como parquet ou Orc.
Isso está na tabela, limpando os dados, eliminando as linhas ausentes, o que quer que você queira fazer.
Tudo o que falamos sobre cola pode ser feito com a formação de lagos.
Ele também pode ajudá-lo a gerenciar o controle de acesso aos dados em seu lago de dados.
Ele pode ajudar na auditoria.
E, na verdade, seu objetivo é guiá-lo pelo processo de criação do seu lago de
dados de forma segura.
Portanto, vamos falar sobre isso de um ponto de vista mais conceitual.
Basicamente, você terá um grande lago de dados S3 quando terminar, certo?
Portanto, a formação de lagos vai se sentar ao lado desse lago de dados do S3, ajudá-lo a criá-lo
e a mantê-lo no futuro, de modo que ele possa usar como fonte de dados qualquer coisa no S3, desde um banco de dados relacional
que você possa ter ou até mesmo fontes de dados NoSQL.
E eles também podem estar no local.
Ele ainda não precisa estar no AWS.
Portanto, mais uma vez, o objetivo da formação do lago é ajudá-lo a configurar esse lago de dados, e
esses dados podem vir de outro lugar dentro da formação do lago.
Você pode configurar todos os rastreadores e trabalhos de ETL e catálogos de dados e segurança e controle de acesso, qualquer
limpeza ou transformação de dados, inclusive para parquet ou ORC.
Novamente, basicamente qualquer coisa que a cola possa fazer.
Você pode configurá-lo como parte da formação de lagos e, depois de configurá-lo, ele pode se integrar facilmente
ao Athena ou ao Redshift ou ao redshift spectrum.
Assim, o Athena e o Redshift podem consultar esses dados automaticamente.
Se você tiver tudo registrado na formação do lago, e um recurso relativamente novo em 2020 é que o EMR também pode se comunicar
diretamente com a formação do lago.
Precificação A formação do Lake em si não custa nada, mas os serviços subjacentes sim.
Obviamente, isso inclui glue, S3, EMR, Athena e Redshift.
Serão cobradas as taxas normais para o que você construir com ele.
O processo de criação de um lago de dados usando a formação de lagos é um pouco mais complicado do que você imagina.
Ele realmente não faz tudo para você.
É por isso que se diz que leva dias e não apenas minutos.
Basicamente, é preciso começar criando um usuário IAM para uma função de analista de dados.
Você conhece a pessoa que usará esse lago de dados e o construirá.
Em seguida, você precisa criar uma conexão colada com a fonte ou fontes de dados de entrada.
Crie um bucket S3 para o próprio lago.
Depois de fazer isso, você pode registrar esse caminho S3 na formação do lago e começar a conceder
permissões a ele.
Portanto, é aqui que a formação de lagos começa a ser útil.
Em seguida, você cria um banco de dados na formação do lago para o catálogo de dados subjacente e concede as permissões
necessárias a ele.
E, nesse ponto, você pode começar a usar blueprints para criar fluxos de trabalho, por exemplo, fazer snapshots de banco
de dados, o que quer que você queira fazer para transformar esses dados e colocá-los em seu data lake.
Em seguida, você executa o fluxo de trabalho e concede permissões selecionadas a quem precisa acessar
os dados resultantes do Lake Athena ou Redshift Spectrum ou, agora, também do EMR.
Em termos conceituais, isso é praticamente tudo o que você precisa saber para o exame.
Às vezes, eles gostam de se aprofundar nessas pequenas questões de solução de problemas e cenários de coisas que
podem dar errado.
Um último ponto com a formação do AWS Lake é a questão das permissões entre contas.
Portanto, se você precisar que pessoas de diferentes contas acessem seu data lake e acessem a formação do lago, é preciso
garantir que o destinatário esteja configurado como administrador do data lake.
Observe também que o AWS Resource Access Manager Ram pode ser uma ferramenta útil para gerenciar contas externas à sua organização
e quais recursos elas podem acessar na sua conta.
Além disso, há permissões de IAM para acesso entre contas que também serão relevantes aqui.
Lembre-se de que a formação de lagos não oferece suporte a manifestos em consultas do Athena ou do Redshift.
Portanto, isso é algo que pode causar erros se você estiver usando um manifesto em uma consulta.
Um aspecto a ter em mente.
Lembre-se também de que as permissões de IAM nas chaves de criptografia do KMS são necessárias para os catálogos de dados criptografados
na formação de lagos, e as permissões de IAM são necessárias para criar blueprints e fluxos de trabalho na formação de lagos.
Portanto, todas essas são possíveis soluções de problemas.
Talvez você queira saber se está encontrando um erro sobre a possibilidade de criar um blueprint ou um fluxo de trabalho.
Provavelmente é um problema do IAM.
Se você estiver tendo um problema de permissão entre contas, provavelmente precisará fazer algo com o Ram.
Portanto, é preciso ter em mente algumas coisas.
Quero dedicar um pouco mais de tempo às permissões de dados na formação de lagos, porque, segundo
consta, isso aparece no exame em alguns lugares.
Então, vamos nos aprofundar um pouco mais.
A formação de lago facilita a definição de permissões em seus dados subjacentes no S3.
Portanto, essa costuma ser uma forma de impor um controle realmente refinado.
Temos a capacidade de restringir as permissões até o nível da coluna, usando apenas a interface do usuário que você
vê aqui à direita, que é muito fácil de usar.
Portanto, apenas estudando essa tela da interface do usuário, você pode entender muito bem quais são os recursos.
Começando pela parte superior, você pode ver que pode vincular suas permissões a usuários do IAM, ou funções
a usuários e grupos do Saml, ou a contas externas do AWS.
Mesmo essas são possíveis, e você pode simplesmente criar uma lista das diferentes diretorias
às quais deseja vincular um conjunto específico de permissões.
Ele permite que você use tags de política, se desejar, e isso pode ser vinculado a bancos de dados, tabelas ou colunas.
E você pode basear sua segurança nessas tags.
Essa é sempre uma boa prática.
Ou você pode simplesmente definir explicitamente as permissões com base em uma tabela ou em colunas específicas dentro
da tabela abaixo.
E você pode ver que há uma interface de usuário muito útil para dizer: você quer permitir que eles façam seleções, inserções,
exclusões ou qualquer outra coisa que você possa imaginar para uma tabela específica, ou mesmo para colunas específicas
em uma tabela?
Portanto, se você tiver dúvidas sobre a implementação da segurança baseada em colunas em seu lago de dados.
A formação de lagos pode ser a melhor maneira de fazer isso.
