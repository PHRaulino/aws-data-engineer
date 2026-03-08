Agora, esse é um novo recurso para 2023, portanto, não esperaria vê-lo no exame até 2024 ou mais.
Mas se estiver assistindo a isso, preste atenção.
E mesmo que não seja, é bom saber disso.
Porque se você quiser usar esse material no mundo real, é bom saber quais ferramentas estão à sua disposição.
A ideia aqui é que você possa executar um notebook Jupyter que tenha o Spark ativado diretamente no console
do Athena.
Assim, você pode ver conceitualmente como isso funciona.
No diagrama superior à direita, ele se parece muito com o Amazon Athena.
Mas, basicamente, você tem um lago de dados no S3 que pode ter um catálogo de dados colados da AWS que transmite
algum tipo de estrutura e esquema a esses dados no S3.
Em seguida, você pode usar o Amazon Athena para Apache Spark para explorar e preparar seus dados de forma interativa, usando
apenas um notebook incorporado ao console do Athena.
Com isso, você pode criar seus aplicativos para analisar e visualizar seus dados nesse notebook e integrar-se
a outras ferramentas de aprendizado de máquina para explorar esses dados ou transferi-los para outra parte do pipeline.
Certo?
Esses notebooks, a propósito, podem ser criptografados automaticamente ou com sua chave KMS.
E, como o próprio Athena, essa é uma solução totalmente sem servidor, portanto, você não precisa pensar
nos servidores subjacentes que estão executando o Spark ou o notebook Jupyter.
Bem, mais ou menos.
Falaremos sobre isso em um minuto.
Ainda precisamos pensar na capacidade.
Basicamente, a maneira como isso funciona é quando você está no Amazon Athena, que normalmente é apenas um mecanismo de consulta
SQL para seus dados não estruturados.
Em vez de selecionar o Athena SQL como seu mecanismo de análise, basta selecionar o Apache Spark.
Eles também têm uma opção para um exemplo de notebook que você pode ver no diagrama.
Se você ativar essa opção, poderá começar com alguns exemplos de código úteis para consultar
os dados no Athena e fazer coisas com eles. Por trás disso, ele usa algo chamado firecracker para ativar rapidamente os
recursos subjacentes do Spark.
Portanto, em vez de ficar esperando que novos servidores sejam provisionados para o spark, isso acontece praticamente
de imediato, pois ele usa algo chamado firecracker para acelerar esse processo.
Há também uma API e uma interface de linha de comando para acessar o Athena for spark.
Você pode usar comandos como criar grupo de trabalho, criar notebook, iniciar sessão ou iniciar execução
de cálculo para fazer tudo isso a partir de uma API ou de uma linha de comando.
E, para isso, basta passar o código do notebook como um parâmetro para dizer create
notebook.
Agora você pode ajustar o Dpus, as unidades de processamento de dados do Athena, para os tamanhos do coordenador e do executor
do seu cluster spark subjacente.
Portanto, embora estejamos dizendo que é sem servidor, você ainda deve pensar na capacidade da CPU pela qual
deseja pagar, basicamente.
Portanto, você pode definir alguns limites superiores para a capacidade que deseja usar.
O preço será baseado em seu uso total de computação e também no número de unidades de processamento de dados
de GPUs por hora.
Falaremos sobre isso com mais detalhes quando falarmos mais profundamente sobre o Athena.
