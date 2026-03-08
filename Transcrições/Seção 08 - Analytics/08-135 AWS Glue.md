que é um sistema para criar suas definições de tabela e executar
ETL (extração, transformação e carregamento) de seus
dados automaticamente.
Agora, a cola é um grande negócio no exame no momento.
Assim, quando removeram todo o conteúdo de aprendizado
de máquina do exame de Big Data da AWS, que na época era chamado de
exame próprio de aprendizado de máquina, eles
preencheram essa lacuna principalmente com mais
conteúdo sobre Glue e Redshift.
Portanto, o Glue realmente desempenha um papel importante no exame de hoje,
por isso é muito importante prestar atenção a essa seção.
Não há muito que você precise saber sobre o Glue,
mas é necessário internalizá-lo e entender como
ele conecta todos esses serviços diferentes
e como pode ser usado como parte de aplicativos maiores.
Então, do que se trata o Glue?
Bem, é um sistema sem servidor, portanto, novamente,
não há nada que você precise manter
lá, que tratará automaticamente
da descoberta e da definição de definições de tabela e esquema.
Portanto, seu principal uso é servir
como um repositório central de metadados para seu lago de dados.
Ele descobrirá esses esquemas a partir de seus dados não estruturados
armazenados no S3 ou em outro local e publicará definições
de tabela para uso com ferramentas
de análise, como Athena, Redshift ou EMR.
Portanto, novamente, o objetivo do Glue em si é extrair a estrutura
dos dados não estruturados.
Se você tiver dados armazenados em um data
lake no S3, ele poderá fornecer um esquema para que
você possa consultá-los usando SQL ou ferramentas semelhantes a SQL, incluindo
RDS e Redshift e Athena e Amazon EMR, e praticamente
qualquer outro banco de dados SQL que possa
usar um esquema como esse.
Outra coisa que o Glue faz são trabalhos de ETL personalizados.
Assim, quando ele descobre esse esquema,
pode fazer algum processamento para você, e isso
pode ser acionado com base no momento em
que os dados são recebidos ou em uma programação ou sob demanda.
E ele é totalmente gerenciado, portanto,
novamente, não há serviços para você manter,
nem hardware para você manter.
Os trabalhos de ETL usam o Apache Spark como base.
Ainda não falamos sobre isso,
mas o Spark é um sistema muito popular para processamento
de dados distribuídos, mas você não precisa gerenciar
o cluster do Spark, o que é muito bom.
Assim, você tem todo o poder do Apache Spark com
o Glue ETL sem precisar gerenciar o cluster do Spark,
o que é muito, muito bom.
Portanto, uma parte dele é o rastreador
Glue e o catálogo de dados que ele preenche.
Portanto, o objetivo do rastreador do Amazon
Glue é examinar os dados no S3 e, muitas
vezes, ele deduzirá esse esquema automaticamente
com base nos dados que vê ali.
Mas, às vezes, é preciso dar algumas dicas.
Você pode programar isso para ser executado periodicamente, se necessário.
E o que isso faz é preencher o catálogo de dados do Glue.
Portanto, temos dados armazenados no S3,
e o Glue pode periodicamente ou sob demanda verificar esses dados e
construir um esquema deles.
E, novamente, essa é apenas a definição da tabela,
quais são as colunas de dados nessas informações que você
armazenou de maneira não estruturada, quais
são os tipos de dados, coisas desse tipo.
Nomes de coluna, ele também pode inferir isso,
onde está armazenado, todas essas informações também são importantes.
E ele usa essas informações para permitir que coisas como
Redshift, Athena ou sistemas que executam um EMR como o Hive
consultem seus dados não estruturados no S3 como
se fossem dados estruturados,
como se fosse um banco de dados relacional tradicional.
Agora, os dados em si permanecem onde estavam originalmente.
Portanto, os dados permanecem no S3.
Você não está duplicando esses dados,
não estamos copiando-os para uma tabela
de banco de dados real em outro lugar.
Estamos apenas usando o Glue para basicamente fornecer
a cola entre essas interfaces de banco de dados relacionais
e o lago de dados não estruturados
que está aqui no S3.
Uma vez catalogados, esses dados ficam imediatamente
disponíveis para análise e, mais adiante, desenvolveremos
e detalharemos muito mais esses sistemas.
E depois que você tiver esses
dados em algo como o Athena, poderá usar
algo como o Amazon QuickSight para
visualizar esses dados.
Portanto, o Glue, mais uma vez, é a cola entre seus dados não estruturados
e as ferramentas de análise de dados estruturados.
Então, vamos falar rapidamente
sobre as partições Glue e S3.
Portanto, não é totalmente mágico.
Você precisa pensar em como vai
estruturar seus dados não estruturados.
Sei que isso soa como um retrocesso,
mas a maneira como você organiza seus dados
afetará a eficiência com que o Glue pode trabalhar
e a eficiência com que seus sistemas podem consultar
esses dados não estruturados.
Agora, o rastreador do Glue extrairá partições de seus dados com
base em como os dados do S3 estão organizados.
Portanto, você deve pensar antecipadamente
sobre como consultará seu data lake no S3 e o que
essas partições devem representar para obter
o melhor desempenho.
Então, por exemplo, vamos imaginar que você tenha dispositivos
enviando dados de sensores para o seu sistema,
para o seu lago de dados a cada hora, simplesmente
despejando dados brutos no S3.
Então, pense em como você vai usar esses dados.
Você está fazendo consultas principalmente por intervalos de tempo?
Nesse caso, você deseja fazer a partição com base
nesses intervalos de tempo, certo?
Portanto, você deve organizar seus buckets do S3 como ano, seguido
de mês, seguido de data,
seguido de dispositivo, certo?
Dessa forma, podemos começar a reduzir
os dados por ano, por mês, por data
e, finalmente, pelo dispositivo
que gerou esses dados.
Isso permitirá que as partições realmente nos permitam
acessar com eficiência os dados de uma determinada data sem
ter que vasculhar todas as outras informações
de outras datas que não nos interessam.
Por outro lado, se estiver fazendo consultas principalmente por dispositivo
e não por tempo, talvez seja melhor colocar o dispositivo primeiro.
Dessa forma, sua partição primária seria o ID do dispositivo
e, em seguida, o ano, o mês e a data.
Portanto, se você for consultar
dispositivos individuais específicos o tempo todo,
e essa for a principal coisa que você quer particionar, é melhor
fazer com que esse seja o bucket de nível
superior no qual você está organizando seus dados no S3.
Então, isso é algo que você pode ver no exame,
qual é a maneira ideal de organizar os dados que estão sendo
armazenados no S3 de modo que o Glue possa extraí-los e apresentá-los
como partições que façam sentido para o que você
vai fazer com eles.
