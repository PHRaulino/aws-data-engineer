Então, você deve
quando estava falando sobre o suporte ACID no Athena.
E você pode dizer: "Espere, o que é o Apache Iceberg?
Talvez você não esteja familiarizado com isso.
Portanto, uma breve introdução: o Apache Iceberg é um formato de tabela para lagos de
dados em grande escala e foi projetado
para lagos grandes, potencialmente em escala de petabytes.
Originalmente, ele foi criado pela Netflix
para resolver seus próprios problemas de processamento
de dados, mas seu código foi aberto,
de modo que qualquer pessoa pode usá-lo agora, inclusive a AWS.
O diferencial do Iceberg é que ele oferece conformidade com ACID, o
que significa que você pode ter consistência transacional para quaisquer
adições, remoções e modificações nos arquivos
do seu lago de dados.
Portanto, isso pode ser um problema se
você tiver vários produtores e consumidores em seu lago de
dados que estejam brigando entre si.
Ele pode garantir que tudo seja consistente
e adequadamente atômico durante essas operações.
Essas atualizações e exclusões em nível de linha também podem
ser importantes especificamente para a conformidade
com o GDPR, que é parte do que está impulsionando
a popularidade do Iceberg atualmente.
Ele também fornece mecanismos para a evolução do esquema, para
facilitar a alteração do esquema de seus dados e o formato de suas tabelas,
além de adicionar novas colunas e excluí-las, o que for necessário
fazer com segurança à medida que os dados evoluem.
Portanto, anteriormente, poderia haver problemas em que,
se você restaurasse uma coluna excluída anteriormente,
ela poderia ter dados
do tipo zumbi e coisas do gênero.
O Iceberg garante que coisas desse tipo não aconteçam,
e também facilita a realização de ações
por meio de uma consulta em vez de algo de nível inferior.
Ele também tem recursos de particionamento.
Portanto, novamente, apenas por meio de uma consulta,
você pode alterar o particionamento dos dados subjacentes.
Ele pode suportar a evolução da partição,
alterá-la ao longo do tempo, se necessário,
atualizar os esquemas de partição
conforme necessário, e também atualizar
os volumes de dados ao longo do tempo com
muita facilidade.
Também importante, ele suporta a consulta de viagem no tempo.
Isso significa que você pode realmente consultar
seus dados como eram em um momento específico no passado, e você pode
ver como isso pode ser útil.
Você pode usar isso para verificar as alterações entre as atualizações
ou simplesmente voltar e fazer uma consulta com base em
como as coisas eram em um determinado momento no passado.
Isso pode ser útil.
Ele também é útil para fazer uma reversão fácil,
portanto, se você precisar reverter
sua tabela para algum ponto no tempo, os recursos de viagem no
tempo do Iceberg simplificam isso.
Ele também oferece gerenciamento
eficiente de metadados, em um nível mais ou menos
elevado, e funciona com
Spark, Flink, Trino, Presto e Hive.
E, é claro, o Spark é algo
que você pode usar no ecossistema
da AWS no EMR ou até mesmo no SageMaker.
Porém, mais recentemente, ele também
está integrado diretamente ao AWS Glue, ao Amazon EMR e ao Amazon Athena.
Então, foi sobre isso que falamos anteriormente,
como você pode usar o Athena com o Iceberg para dar suporte
à conformidade com ACID.
Então, vamos falar um pouco mais sobre como isso funciona.
A propósito, esta pequena captura de tela
à direita é da interface de criação de notebook do Amazon Athena.
E você pode ver que, ao criar um novo notebook,
é possível especificar o Apache Iceberg como um
dos formatos de tabela que você pode escolher.
Portanto, é aí que você veria o Iceberg aparecer
na interface do usuário real.
Então, como tudo isso se encaixa?
Então, vamos dar uma olhada no diagrama à direita aqui.
Isso resume tudo.
Então, basicamente, você pode usar o AWS Glue no lugar do Hive, que é o que o Iceberg
normalmente usa como fonte
dos metadados da tabela.
Então, na parte superior, você tem o Spark, o Trino,
o Flink ou talvez até o Athena, certo?
E isso é feito por meio da API do Iceberg,
que é apenas uma API que o Iceberg fornece
para interagir com tabelas formatadas pelo Iceberg.
E agora, em vez do Hive, que
é o que normalmente usamos por padrão,
vamos substituir o catálogo Glue da AWS como o armazenamento
de metadados.
E, como veremos, há algumas etapas de migração
que você precisa fazer para tornar
o catálogo do Glue compatível com o Iceberg, mas isso
pode ser feito.
Assim, o Iceberg se comunicará com o catálogo
Glue para obter metadados sobre os
dados, quais são os nomes das colunas,
como eles estão dispostos, tudo isso, quais são os tipos
de dados e, em seguida, também se comunicará com o Amazon S3
para o armazenamento de dados subjacente real em seu data lake.
Portanto, a API do Iceberg está se comunicando
com o catálogo do Glue para obter esses metadados.
Você recuperará e armazenará dados do Amazon S3 e, normalmente,
eles estarão no formato Parquet para serem otimizados
para colunas e mais eficientes para uso com o
Iceberg.
E, em seguida, o Spark, o Flink ou qualquer
outro pode se sentar em cima da API do
Iceberg para fazer todas as suas coisas em conformidade com a ACID.
Então, novamente, o Athena também pode estar no topo agora, e você
pode ver como isso vai usar o Iceberg como um meio
de implementar a conformidade ACID do Athena.
Assim, com o Athena na parte superior, em
vez do Spark ou outro, você pode
ver que ele pode simplesmente
confiar na API do Iceberg para obter a conformidade com ACID
e todos os outros recursos
que o Iceberg oferece basicamente de graça, desde
que você tenha um catálogo Glue subjacente que
tenha sido migrado para ser compatível com o Iceberg.
Então, como é isso?
Portanto, há algumas maneiras de fazer essa migração.
Os catálogos de dados do Glue devem ser compatíveis
com a API do Iceberg para serem usados com o Iceberg.
Portanto, isso não acontece de imediato.
Mas, depois que você fizer isso, o Athena, o Spark
e qualquer outra coisa poderá usar o Iceberg como intermediário para
transações de ativos e tudo o mais.
Ele também pode lhe proporcionar conformidade,
como falamos, o GDPR pode precisar desse tipo de coisa.
Ele permite que você
faça coisas como expirar versões antigas de tabelas
e também ter trilhas de auditoria
que podem ser exigidas por vários regulamentos.
Ele também pode fornecer relatórios
históricos com consultas de viagem no tempo
e resolver muitos dos problemas
de consistência que você pode ter com muitos
produtores e consumidores ativos brigando entre si
pelos dados em seu lago de dados.
Portanto, todos esses são bons motivos para fazer isso.
Há algumas maneiras de fazer isso.
Uma delas é a migração no local.
Nessa abordagem, você deixa seus dados
onde estão e não cria uma cópia deles,
apenas cria novos metadados do Iceberg.
Portanto, nesse cenário, você só migrará
os metadados e não o armazenamento de dados subjacente.
Agora, a desvantagem disso é que não
permite nenhuma alteração de esquema ou partição no futuro.
Portanto, essa é uma troca.
No entanto, isso significa que você
não estará duplicando seus dados nesse processo.
Portanto, se você tiver um grande
lago de dados e não quiser pagar pelo dobro do armazenamento,
o in-place pode ser algo a ser considerado.
No entanto, também é possível fazer uma migração de sombra, essa
abordagem copiará os dados e permitirá
que você faça uma validação
adicional ao longo do caminho, além
de facilitar a reversão e a recuperação.
E também revela toda a gama de suporte que
a Iceberg oferecerá a você.
Um pequeno exemplo aqui à direita
do que você pode digitar no editor do Athena Query diretamente na interface
do usuário para fazer
uma dessas migrações de sombra.
E você pode ver que, na verdade, é bem simples.
Basta criar uma nova
tabela com um tipo de tabela de Iceberg e um formato de Parquet
em algum local S3 no qual você a criará.
Então, você pode simplesmente dizer: "Ei,
selecione isso do meu banco de dados
de origem, de onde quer que venha,
e copie-o para o formato
exigido pelo Iceberg".
Portanto, normalmente esse é o caminho a seguir se você puder arcar
com os custos adicionais de armazenamento de dados.
