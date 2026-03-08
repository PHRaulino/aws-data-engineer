O Spectrum permite que você consulte exabytes.
Exabytes, veja bem,
já passamos dos terabytes ou petabytes.
Estamos na terra do big data, com certeza.
Exabytes de dados não estruturados no S3 sem
carregá-los em seu cluster.
Portanto, da mesma forma
que o Athena pode usar o catálogo AWS Glue para criar
tabelas sobre os dados do S3, o Redshift Spectrum
pode fazer a mesma coisa.
É praticamente a mesma ideia.
Só que, em vez de ter
esse mecanismo de SQL de consulta baseado em console no Athena, ele se parece
com outra tabela no seu banco
de dados Redshift.
Dessa forma, você
pode ter tabelas que incorporam seu data lake do S3 juntamente com tabelas
que incorporam dados que estão realmente armazenados
no próprio cluster do Redshift,
e você pode tratá-las como a mesma
coisa e unir-se a elas como quiser.
Então é muito legal.
Ele permite que você execute consultas em
exabytes de dados não estruturados no S3 sem a necessidade
de carregar esses dados no próprio cluster do Redshift
ou de transformá-los de alguma forma.
Ele oferece simultaneidade ilimitada,
permitindo que várias
consultas acessem os mesmos dados simultaneamente no S3.
Ele pode ser dimensionado para milhares de instâncias, se necessário, para que suas
consultas sejam executadas rapidamente, independentemente do tamanho dos dados, e permite
que você separe a capacidade de armazenamento e de computação, possibilitando
dimensionar cada uma delas de forma independente.
Portanto, com o Spectrum, todo o seu armazenamento está sendo feito no S3.
O Spectrum está apenas fazendo a parte computacional
da análise desses dados.
Atualmente, o Redshift
Spectrum é compatível com vários
formatos de dados de código aberto, incluindo AVRO, CSV, Grok,
ION, JSON ORC, Parquet, RCFile, RegX, Serta, SequenceFiles, arquivos
de texto e TSV.
Portanto, praticamente qualquer formato comum de dados de código aberto
que você possa imaginar.
Se você tiver isso em um bucket do S3 em algum lugar,
o Redshift poderá analisá-lo e fazer consultas a ele.
Atualmente, o Spectrum também oferece suporte
à compactação Gzip e Snappy.
Portanto, se quiser compactar seus dados do S3
para economizar espaço e largura de banda, você também pode fazer isso.
Portanto, eles pensaram em praticamente tudo aqui.
Voltando ao Redshift como um todo, como
o Redshift é tão rápido?
Bem, novamente, ele usa processamento paralelo
massivo ou MPP para fazer isso.
As cargas de dados e consultas são distribuídas automaticamente
entre todos os nós, e a adição de nós ao data warehouse
é facilitada e também permite um desempenho rápido
das consultas à medida que o data warehouse
cresce.
Portanto, ele fará todas as suas consultas em paralelo e, se você
precisar de mais velocidade ou mais capacidade,
basta adicionar mais notas ao cluster
e ele aproveitará automaticamente
essa capacidade extra.
Ele também usa colunas ou armazenamento de dados.
Portanto, seus dados são organizados por coluna, já que os sistemas
baseados em colunas são ideais para armazenamento de dados e análises
para consultas a grandes conjuntos de dados, porque, normalmente,
você está apenas analisando colunas específicas de um grande número
de colunas.
Portanto, você pode economizar muita
largura de banda e muito
tempo de pesquisa organizando seus dados por colunas em vez de por linhas.
A coluna ou os dados são armazenados sequencialmente
na mídia de armazenamento e exigem muito menos E/S, melhorando
assim o desempenho da consulta.
E ao usar coluna ou armazenamento, cada
bloco de dados armazena valores
de uma única coluna de várias linhas.
Assim, à medida que os registros entram no
sistema, o Amazon Redshift converte os dados de forma transparente
em armazenamento colunar para cada uma das colunas.
Isso o ajuda a evitar a varredura
e o descarte de linhas indesejadas.
Agora, os bancos de dados colunares geralmente não são adequados
para OLTP, o processamento de transações on-line.
Portanto, lembre-se de que um antipadrão para o Redshift é o OLTP.
Ele é usado para OLAP, como qualquer data warehouse.
O Redshift usa um tamanho de bloco de um megabyte, o que é mais eficiente
e reduz ainda mais o número
de solicitações de E/S necessárias para realizar qualquer
carregamento de banco de dados ou outras operações que fazem parte
da execução de uma consulta.
Ele também pode fazer a compactação de colunas.
Portanto, em comparação com os armazenamentos
de dados baseados em linhas, os armazenamentos de dados colunares geralmente podem
ser muito mais compactados, pois tudo é armazenado sequencialmente
no disco no mesmo tipo de formato de dados.
Várias técnicas de compactação são frequentemente aplicadas
para obter melhores resultados.
Assim, não são necessários índices ou visualizações materializadas com o
Redshift e, portanto,
ele usa menos espaço em comparação com os sistemas
de banco de dados relacionais tradicionais.
Ele fará uma amostragem automática dos dados
e selecionará o esquema de compactação mais adequado
quando os dados forem carregados em uma tabela vazia.
A compactação é uma operação em nível de coluna
que reduz o tamanho dos dados quando eles são armazenados.
A compactação pode conservar o espaço de armazenamento
e reduzir o tamanho dos dados que são lidos no armazenamento.
Isso reduz a quantidade de E/S do
disco e, portanto, melhora o desempenho da consulta.
Portanto, quando estiver carregando dados em um cluster do Redshift,
geralmente você usa o comando Copy para fazer
isso de forma mais eficiente.
Isso permite que você copie dados para o cluster
de forma distribuída e paralela.
E quando você emitir esse comando Copy,
ele analisará e aplicará a
compactação automaticamente.
Você não precisa fazer nada, ele simplesmente faz isso por você.
Mas se você quiser ter uma ideia do que está acontecendo,
ele oferece um comando de análise de compactação, que executará
a análise de compactação e produzirá um relatório
com a codificação de compactação sugerida para as tabelas
analisadas.
