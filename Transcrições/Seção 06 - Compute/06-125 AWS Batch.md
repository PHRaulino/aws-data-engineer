O próximo serviço
que você precisa conhecer em alto nível é o AWS Batch.
O AWS Batch permite que você execute trabalhos em lote,
como o próprio nome indica,
e eles são baseados em imagens do Docker.
Portanto, com o AWS Batch, você não provisiona a instância.
Há um provisionamento dinâmico das instâncias para
você, seja uma instância EC2 ou uma instância Spot.
E o Batch calcula a quantidade ideal e o tipo
dessas instâncias com base no volume
de trabalhos que precisa fazer e nos
requisitos.
Portanto, você não precisa gerenciar nenhum cluster.
É um serviço totalmente sem servidor, assim como o Glue, você
só paga pelas instâncias subjacentes do
Portanto, você pode programar trabalhos em lote usando os eventos
do CloudWatch para permitir a execução em um cronograma ou pode
orquestrar trabalhos em lote usando funções de etapa.
E veremos isso na próxima palestra.
Mas, uma pergunta que você pode ter novamente
é: "Qual é a diferença entre Batch e Glue? Então, o Glue, mais uma vez, só
para revisar, é o Apache Spark
Code, somente em Scala ou Python,
e seu foco é o ETL.
E você não se preocupa em configurar o gerenciamento
de recursos e tem o catálogo de dados.
Já no caso do Batch, a situação é um pouco diferente.
É para qualquer trabalho de computação, independentemente do trabalho, certo?
Não se trata apenas de
ETL, mas de qualquer coisa que seja orientada para lotes.
Portanto, desde que você tenha uma imagem do Docker que funcione para
o Batch, você pode fazer isso no Batch.
Assim, por exemplo, um trabalho que pode ser bom para o Batch,
seria uma tarefa de limpeza em um bucket S3.
Então, você executa um script em um bucket S3 para limpá-lo
e executa isso como um trabalho em lote de vez em quando.
Já no Glue, trata-se realmente de pegar os dados,
transformá-los e colocá-los em outro lugar.
Assim, os recursos são criados em suas contas e são
gerenciados pelo Batch,
de modo que você está usando instâncias do EC2 em sua conta
e, portanto, tem acesso a todos os recursos em suas contas.
Portanto, se você tem um ETL que significa que você
realmente precisa transformar alguns dados, o Glue
provavelmente será uma escolha melhor.
Mas se você tiver um trabalho não relacionado
a ETL, mas ainda assim orientado
a lotes, o AWS Batch será melhor.
Portanto, isso é tudo apenas para esse serviço.
Espero que tenha sido
útil e vejo você na próxima palestra.
