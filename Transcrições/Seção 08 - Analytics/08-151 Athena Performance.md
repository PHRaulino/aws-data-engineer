Algumas
do Athena, o exame adora focar em tópicos como esse.
Basicamente, isso se resume a três coisas sobre
as quais queremos falar aqui.
Uma delas é que, em geral, você obterá melhor
desempenho usando formatos de dados colunares, como ORC ou Parquet.
O Athena funcionará melhor
se você puder pré-processar seus dados de
alguma forma para que fiquem em um formato
colunar, e você pode fazer isso com coisas
como o Glue ou por meio de uma transformação ETL.
Há muitas ferramentas que você pode usar
para transformar seus dados em um formato
mais otimizado para o uso do Athena.
Portanto, se estiver preocupado com o desempenho, certifique-se
de que está usando um formato de dados colunar
com o Athena em ORC ou Parquet.
Portanto, se estiver atingindo os dados do S3, se já estiverem
nesse formato, você economizará um pouco de trabalho.
Além disso, lembre-se de que um pequeno número
de arquivos grandes geralmente terá um desempenho melhor do
que um grande número de arquivos pequenos com o Athena.
Portanto, se você puder ter um pequeno número
de arquivos de dados colunares grandes, esse
provavelmente
será o seu caso de desempenho ideal.
Além disso, aproveite as partições.
Portanto, se você conseguir organizar seus
dados no S3 em um formato de partição que se alinhe
com a forma como você vai consultar esses dados,
por exemplo, se você estiver acessando seus dados mais comumente por um intervalo de
datas específico ou algo assim, então particionar
seus dados por data faria
muito sentido, certo?
Agora, se você precisar adicionar partições após
o fato, digamos que você tenha um conjunto de dados existente no
S3 que não esteja particionado
e queira melhorar seu desempenho
adicionando partições, não será necessário
começar totalmente do zero.
O que você pode fazer
no Athena é usar um comando chamado MSCK REPAIR TABLE para voltar e adicionar
esses metadados para as partições no Athena.
Portanto, se você precisar adicionar partições
posteriormente a um banco de dados
Athena existente, poderá usar o MSCK REPAIR TABLE para fazer isso.
Esses são os principais pontos sobre o desempenho do Athena.
Lembre-se dessas três coisas
e você estará em boa forma.
