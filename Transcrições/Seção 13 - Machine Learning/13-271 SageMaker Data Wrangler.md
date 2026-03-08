mais diretamente aplicável à engenharia
de dados.
Basicamente, trata-se de um pipeline
de ETL incorporado ao SageMaker Studio.
E, como você pode imaginar, ele tem muito
em comum com o Glue Data Studio.
No entanto, ele é usado para preparar dados
principalmente para aprendizado de máquina, portanto, é personalizado
para pipelines de aprendizado de máquina.
Ele permite que você importe dados de onde quer que eles estejam.
Talvez sejam arquivos CSV no S3 ou streaming, quem sabe?
Ele permite que você visualize esses dados
e se certifique de que está satisfeito com a distribuição
desses dados e saiba sobre quaisquer valores discrepantes
que possam estar ocorrendo antes de inseri-los no modelo de aprendizado
de máquina.
E isso pode transformar seus dados.
Eles têm mais de 300 transformações para escolher,
a partir do Data Wrangler, ou você
pode integrar suas próprias transformações usando o código
PANDAS ou PIs Spark ou PIs Spark SQL se quiser fazer
algo especial.
Outro recurso interessante
é o chamado Quick Model, que
permite treinar o modelo para o qual você
está tentando preparar os dados com um subconjunto
desses dados e medir rapidamente os resultados.
Isso permite que você experimente diferentes
transformações e diferentes
maneiras de preparar seus dados para otimizá-los para o modelo
que você está alimentando, e experimente e descubra quais
são as melhores transformações para produzir os melhores
resultados do modelo a partir do qual você vai
treinar esses dados.
Block Diagram (diagrama de blocos), vamos ver como ele se parece.
Então, basicamente, o SageMaker Data Wrangler fica no meio do
caminho entre as fontes de dados e o local para onde você pode enviá-los.
Você pode ver que ele pode receber dados do S3,
da formação do lago, do Athena, do armazenamento
de recursos do SageMaker, sobre o qual falamos anteriormente, ou
do Redshift ou de qualquer coisa que possa se comunicar com o JDBC.
Isso incluiria coisas como software como serviço,
aplicativos como o Salesforce ou algo assim,
ou talvez sistemas externos como o Databricks.
Depois de passar pelo pipeline do Wrangler de dados,
é possível exportar o código em um Jupyter Notebook que pode
ser usado como parte de um notebook de aprendizado
de máquina para importar, transformar e processar ainda mais os dados.
Portanto, é importante
entender que o Data Wrangler não está realmente fazendo as transformações
do seu pipeline em si, ele está apenas gerando código para fazer
essas transformações no pipeline.
Portanto, pense nele mais como uma ferramenta de geração de código.
No final das contas, esse código pode ter um ponto de extremidade próprio
no qual ele também despeja esses dados.
Talvez ele entre no processamento do SageMaker
da Amazon para treinar um modelo.
Talvez ele vá para os pipelines do SageMaker como
parte de um processo maior, ou talvez volte para o armazenamento de recursos
do SageMaker para disponibilizar esses recursos transformados para
outros modelos.
Vamos dar um exemplo aqui.
Então, é assim que ele se parece. Este é o SageMaker Studio.
Portanto, se quisermos importar dados,
começaremos pela guia de importação aqui em cima.
E, neste exemplo, estamos pegando esse arquivo CSV.
Portanto, estamos especificando um nome de arquivo específico em um bucket S3 específico
com um tipo de arquivo específico.
E você pode ver que ele está pré-visualizando
o que está no arquivo CSV automaticamente,
apenas para ter certeza de que é o que você espera.
Portanto, este é um conjunto de dados que analisamos anteriormente
em nossas atividades de SQL.
O mesmo conjunto de dados aqui, onde temos passageiros do Titanic.
E o conjunto de dados informa quem sobreviveu, quem não sobreviveu,
qual era a classe, você sabe, primeira classe, segunda classe,
terceira classe, o nome e outras informações sobre eles.
Você pode expandir ainda mais essa visualização para ver o que está acontecendo
e realmente ver quais são os tipos de dados que foram
inferidos para cada um deles.
E você pode mudar isso se precisar.
Portanto, se ele errou nos tipos de dados, você
pode alterar isso lá.
Se quiser ter nomes de colunas mais legíveis, você também
pode alterar isso aqui.
Você também pode visualizar os dados
e certificar-se de que a distribuição é a esperada.
Portanto, aqui podemos ver que a idade está seguindo uma
distribuição muito boa.
Na verdade, a tendência é que eles sejam mais jovens do que eu esperava no
Titanic, é apenas uma verificação de sanidade.
Como não se trata de um curso de análise de dados,
não vou me aprofundar muito nesse assunto,
mas ele permite que você visualize as propriedades desses dados e certifique-se
de que eles são o que você espera antes de alimentá-los
em um modelo de aprendizado de máquina.
E então você pode transformar os dados.
Portanto, neste exemplo aqui, estamos pegando a classe
e codificando-a com um hot.
Portanto, essa transformação é chamada de codificação categórica.
Coisa muito comum de se fazer com o aprendizado de máquina.
Portanto, normalmente, com o aprendizado de máquina, você sabe que as entradas
precisam ser esses uns e zeros binários.
Normalmente, você não pode simplesmente alimentá-lo com um número arbitrário.
Portanto, o que faremos é, em vez de passar um recurso para
a classe, que pode ser um, dois ou três,
teremos três recursos diferentes que basicamente
dizem: estou na classe um, estou na classe dois ou estou na
classe três?
E um desses três recursos será verdadeiro
ou um para cada passageiro individual.
Portanto, é isso que o encode categorical faz.
Mas no mundo do aprendizado de máquina,
chamamos isso de codificação quente.
Apenas um exemplo das transformações que você pode fazer e
suas escolhas de como transformar esses dados e como
apresentá-los ao seu modelo podem fazer uma grande diferença
na qualidade desse modelo.
Portanto, aspectos como a forma de
normalizar esses dados também podem ser extremamente importantes.
Ou apenas quais dados você
está fornecendo a ele e quais dados você está retendo no momento.
O que é realmente interessante é que você pode fazer
o que chamamos de modelo rápido para treinar seu modelo usando esses dados, usando
esses dados de transformação.
Assim, você pode testar o quanto suas escolhas de transformação realmente
afetaram o modelo de aprendizado de máquina
no pipeline, o que é algo muito poderoso.
Assim, posso ter certeza de que minhas escolhas de ETL aqui
serão ideais para o modelo no qual estou alimentando esses dados.
E, quando terminar, posso exportar esse fluxo de dados novamente.
Basicamente, tudo o que isso faz é criar código para você.
Portanto, isso produzirá um Jupyter Notebook.
É uma saída, mas basicamente é um código Python que incorpora
todas as etapas de ETL que você acabou de configurar.
Isso permite que você coloque em um Jupyter Notebook, que
é apenas um ambiente para executar o código Python.
O código necessário para extrair esses dados, transformá-los
da maneira que você especificou no Data Wrangler e aplicá-los repetidamente
por meio desse bloco de
código, conforme necessário.
Portanto, mais uma vez, você sabe, o Data Wrangler não
está realmente sentado em seu pipeline,
mas está produzindo código que entra em seu pipeline.
Essa é uma distinção muito importante.
Se você tiver problemas com o Data Wrangler,
há algumas dicas de solução de problemas aqui.
Uma delas é garantir que o usuário do seu estúdio, o SageMaker studio
-: User, tenha as funções IAM apropriadas para o Data Wrangler.
Além disso, é necessário certificar-se
de que suas fontes de dados permitam que o Data Wrangler as acesse.
Portanto, se o Data Wrangler não tiver permissões para
acessar seus dados, isso causará problemas.
Portanto, você precisa se certificar de que qualquer fonte de dados
que tiver tenha a política de acesso total do Amazon SageMaker anexada a ela.
Você também pode se deparar com limites de recursos aqui.
Portanto, se você vir um erro do tipo a
instância a seguir não está disponível, isso provavelmente
não significa que estamos ficando sem instâncias
no AWS, significa apenas que talvez seja necessário solicitar
um aumento de cota para que você possa
usar mais instâncias do que originalmente.
Portanto, se você encontrar esse erro, basta acessar
as cotas de serviço e, lá, acessar
o Amazon SageMaker, acessar os aplicativos
de gateway do Studio Kernel
e solicitar mais ml dot M 5. 4 x instâncias grandes, e há um formulário
para isso.
Alguém precisa aprová-lo.
Mas é isso que a mensagem de erro realmente significa.
Você precisa aumentar sua cota.
Esses são os dados do Wrangler em poucas palavras.
