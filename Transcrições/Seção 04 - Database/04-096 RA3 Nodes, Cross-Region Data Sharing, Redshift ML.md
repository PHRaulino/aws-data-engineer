dos recursos mais recentes do Redshift que foram lançados
nos últimos anos, acho que em 2020 ou no final de 2019, os nós
RA3 foram introduzidos.
Esse é um tipo de nó especial que é otimizado para o Redshift, portanto,
foi um grande negócio, e
eles têm desenvolvido cada vez mais com
base nisso ao longo dos anos.
A grande ideia aqui, no entanto, é que ele vem com
armazenamento gerenciado.
Portanto, eles desacoplaram os recursos
de computação e armazenamento com o nó RA3.
Basicamente, a observação deles foi que os recursos de armazenamento e os recursos
de computação estavam evoluindo em taxas diferentes.
Portanto, com a capacidade de dimensionar independentemente a
capacidade de computação e armazenamento, você pode
usar melhor os recursos que tem para o cluster Redshift.
Portanto, isso é muito importante.
Outra coisa que foi lançada em 2020, acho que
sim, foi a exportação do data lake do Redshift.
E a ideia é que você possa despejar uma consulta do Redshift
diretamente no S3 no formato Apache Parquet.
Portanto, se você tiver uma grande consulta em um
grande data warehouse no Redshift, poderá
despejá-la em um data lake no S3 com bastante facilidade
usando a exportação do Data Lake.
A motivação para fazer isso é que o formato Parquet é duas vezes
mais rápido para descarregar e também
consome até 6 vezes menos armazenamento.
Portanto, é uma maneira muito
rápida e compacta de exportar dados para um lago de dados, e o
lago de dados que você terá será compatível
com o Redshift Spectrum, Athena, EMR ou SageMaker.
Qualquer coisa que possa ler a partir de .
ele também é particionado automaticamente para você.
Portanto, você não precisa necessariamente pensar nisso.
Além disso, mais recentemente, em 2022 ou no final de
2021, eles introduziram tipos de dados espaciais.
Portanto, agora há tipos de dados
de geometria e geografia disponíveis no Redshift.
Portanto, se você precisar fazer coisas com o mapeamento
desses tipos de aplicativos,
poderá fazer isso no Redshift agora com esses novos tipos de
dados e também um novo recurso é o compartilhamento de dados entre
regiões, novo para 2022.
Ele vem evoluindo ao longo
do tempo, mas está evoluindo mais ultimamente.
A ideia aqui é que você possa compartilhar dados em tempo real entre
Clusters Redshift sem precisar copiá-los.
Por isso, falamos muito sobre a replicação de dados em
diferentes regiões e diferentes entidades
e como isso pode ser um problema.
Assim, com o compartilhamento de dados entre regiões, eles realmente
se esforçaram para simplificar isso o máximo possível.
Isso permite que você, novamente, compartilhe dados
em tempo real entre regiões.
Isso é uma novidade.
E até mesmo entre contas, se você quiser, de maneira
segura e muito fácil.
Para fazer isso, você precisa
usar o novo tipo de nó RA3 sobre o qual falamos.
Ele só é compatível com nossos tipos de nós RA3, o que é muito importante:
compartilhamento de dados entre regiões, uma nova
maneira fácil de gerenciar esse problema.
Outro recurso mais recente é o Amazon Redshift ML ou Machine
Learning.
Não vou me aprofundar muito nisso porque, de
modo geral, os tópicos de aprendizado de máquina
estarão no exame de aprendizado de máquina, não no
exame de análise de dados, mas, ainda assim,
você deve pelo menos saber que isso existe, pois
pode ser mencionado no exame.
Isso foi introduzido em meados de 2021, portanto,
é um jogo justo neste momento.
Conceitualmente, há esse diagrama de alto nível
que a Amazon nos fornece e que diz que você começa
coletando seus dados em um data warehouse,
que provavelmente é o S3, e, em
seguida, o Redshift ML engloba todo esse sistema em que você está criando
um modelo de aprendizado de máquina apenas usando
um comando SQL usando Criar modelo automaticamente, que será iniciado
no Amazon SageMaker para ajustar e treinar automaticamente seu
modelo.
Especificamente, ele está usando o piloto automático
do SageMaker, mas vou explicar isso em um segundo.
Em seguida, ele implantará seu modelo.
Portanto, você pode simplesmente usá-lo com comandos
SQL no Redshift para obter previsões em tempo real usando comandos SQL.
Portanto, na prática, você começaria
fazendo com que o Redshift
exportasse os dados de treinamento do seu modelo de
aprendizado de máquina para o Amazon S3.
O SageMaker Autopilot é a tecnologia específica
que ficará ali, na seção
de trem deste diagrama, e pré-processará
seus dados e tentará encontrar
os parâmetros ideais do PyPI, o melhor modelo a ser usado
e os melhores parâmetros
para esse modelo.
Depois que o modelo tiver sido treinado,
ele poderá fazer previsões e o Redshift simplesmente
registrará a função de previsão como uma função
SQL no cluster do Redshift.
Assim, você pode ir em frente e acessar o banco de dados do
Redshift para obter previsões com base no modelo que você
treinou e implantou usando o Redshift Machine Learning.
Agora, quando você cria um modelo, isso dá início
a uma série de coisas por trás do capô, certo?
Ou seja, a criação e o treinamento de um modelo de aprendizado
de máquina podem ser computacionalmente intensivos, e isso custa dinheiro.
Portanto, você verá um item de linha separado no SageMaker da
Amazon em sua fatura do AWS se estiver usando o Redshift ML.
Você também pagará por qualquer armazenamento subjacente
usado no S3 para armazenar os
dados de treinamento e os dados que precisam
ir e voltar entre o Redshift
e o SageMaker durante todo o processo.
Em resumo, esse é o Redshift ML.
Novamente, não é algo com o qual você provavelmente terá
que se preocupar muito para o exame, mas, para fins de conclusão,
esse é um recurso importante do Redshift.
