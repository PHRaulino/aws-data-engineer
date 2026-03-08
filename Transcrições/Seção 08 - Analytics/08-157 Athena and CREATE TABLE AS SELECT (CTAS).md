Vamos
Você provavelmente verá
isso no contexto do Amazon Athena,
embora isso também ocorra em outros bancos de dados.
No entanto, a sintaxe pode ser um pouco diferente.
Muito semelhante em espírito
a uma visualização materializada no Redshift,
ele cria uma nova tabela a partir dos resultados da consulta.
Portanto, você pode fazer qualquer instrução SELECT que
possa imaginar e criar uma nova tabela a partir do resultado dessa consulta.
E talvez você possa usar isso para criar uma nova tabela
que seja um subconjunto de outra tabela.
Assim, posso dizer: "Ei, vou fazer um SELECT
dessa tabela antiga para algum subconjunto
do que está nessa tabela e criar uma nova tabela
com base no resultado da consulta. No entanto, esse também é um pequeno
truque para converter dados
em um novo formato subjacente.
E isso é especialmente interessante, lembrando
que o Athena pode ficar em cima de um lago de dados no S3.
Portanto, você poderia usar isso como uma forma de converter os dados no S3 em
um formato totalmente diferente, que poderia
ser mais eficiente para o Athena, certo?
Então, por exemplo, vamos dar uma
olhada nesses dois exemplos abaixo.
Na tabela da esquerda,
estamos dizendo CREATE TABLE new table WITH format equals Parquet,
write compression equals SNAPPY AS SELECT
star FROM old table.
Então, o que está acontecendo aqui?
Vamos selecionar tudo da tabela antiga e vamos
reescrevê-la em uma tabela chamada
nova tabela.
Mas, ao longo do caminho, vamos alterá-lo para Parquet, que é
um formato colunar que será mais bem otimizado para fazer
consultas no Athena, e também
com a compactação SNAPPY para
otimizá-lo ainda mais.
Portanto, essa é uma maneira fácil e rápida de compactar ou alterar o formato
de seus dados brutos no S3 e transformá-los em
algo que funcione de forma muito
mais eficiente com o Athena.
Outro exemplo à direita aqui, estamos com o mesmo espírito,
selecionando tudo da tabela antiga
e colocando em uma nova tabela chamada my orc ctas table.
Nesse caso, não apenas estamos mudando o formato
para ORC ao longo do caminho, mas
também estamos especificando um novo local externo.
Então, estou dizendo:
"Ok, não só quero alterar o formato
dessa tabela, como também vou armazená-la explicitamente
nesse caminho S3 dentro do meu bucket de resultados do Athena. Certo?
Portanto, esse é um tipo de truque de finalização,
porque não só estamos mudando a forma como ele é exposto
ao Athena, mas também estamos mudando e armazenando
os dados brutos subjacentes nessa outra tabela no
S3.
Portanto, essa pode ser uma maneira rápida
e suja de fazer transformações de dados ou transformar o formato
real dos dados subjacentes, os dados
brutos, em outra coisa usando apenas o Athena.
Em seguida, posso ir até o balde S3
e retirá-lo de lá, se quiser.
Portanto, CREATE TABLE AS SELECT é um truque
muito útil para converter dados em algo mais eficiente
e, talvez, até mesmo colocá-los em algum lugar onde você
possa obtê-los mais tarde.
Não se esqueça disso.
