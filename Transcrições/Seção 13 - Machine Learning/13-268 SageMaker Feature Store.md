Como dissemos, o aprendizado
do exame de engenharia de dados.
No entanto, há alguns componentes do SageMaker que estão
diretamente relacionados à engenharia de dados.
Então, vamos dar um zoom e focar nesses recursos.
Um desses recursos é chamado de SageMaker Feature Store,
e a palavra recurso tem um sentido diferente.
Portanto, nesse contexto, um recurso é uma propriedade usada para treinar um modelo
de aprendizado de máquina.
Por exemplo, se você estiver tentando prever
o partido político de alguém com base em recursos.
Esses recursos podem ser o endereço de alguém, sua renda,
sua idade, coisas desse tipo.
Seus recursos são, na verdade, apenas colunas ou campos
em uma linha em que você está usando essas informações
para tentar prever um rótulo para essa linha.
Portanto, os recursos, nesse caso, podem ser as propriedades
dessa pessoa, como endereço, renda ou idade, e
o rótulo que estamos tentando
prever é o seu partido político, nesse exemplo.
Mas é isso que queremos dizer com recursos nesse contexto.
Os modelos de aprendizado de máquina exigem acesso rápido e seguro a esses dados
de recursos para treinar um modelo de aprendizado de máquina.
Como você pode imaginar, ele precisa sugar esses dados em quantidades
muito altas e com muita rapidez, e também precisa fazer
isso de forma segura, pois algumas dessas
informações podem ser confidenciais
ou pessoais.
Também é um desafio manter esses dados organizados e
compartilhar esses recursos em diferentes modelos.
Portanto, você quer evitar uma situação em
que esteja armazenando esses recursos mais de uma vez.
Você quer poder compartilhá-los quando
estiver tentando fazer coisas diferentes com o aprendizado de máquina;
a origem desses recursos depende totalmente de você.
Você pode ver que o SageMaker Feature Store fica
mais ou menos no meio de todo esse universo de onde
os dados podem vir.
Talvez seja proveniente do SageMaker
Studio, talvez seja proveniente de um pipeline, como funções de etapa,
pipelines do SageMaker ou Apache
Airflow, em que as coisas são simplesmente despejadas lá.
Ao longo do caminho, seus recursos podem estar vindo de algum
tipo de pipeline de EMR ou do Glue ou do processamento do SageMaker.
Talvez esses recursos estejam sendo transmitidos pelo Kinesis ou
pelo Kafka e talvez estejam sendo criados pelo SageMaker Data Wrangler
ou pelo Glue Data Brew, certo?
Todos esses são exemplos de onde a data Make pode vir.
Portanto, sua origem pode estar em praticamente qualquer lugar.
O que o FE Feature Store traz para
a mesa é a organização desses dados.
Portanto, ele tem um armazenamento de recursos
e, dentro de um armazenamento de recursos,
temos o que chamamos de grupos
de recursos, onde organizamos esses recursos juntos,
e cada grupo de recursos conterá identificadores de registros, nomes de recursos
e horários de eventos associados a esse recurso.
Como tudo isso funciona? Portanto, há basicamente um mundo de streaming e um mundo
de lote aqui com o armazenamento de recursos do State SageMaker.
Então, vamos imaginar que estamos transmitindo dados do
Kinesis ou do MSK ou do Apache Spark ou do SageMaker Data Wrangler ou de qualquer outra
fonte de transmissão.
Basicamente, há um registro de colocação, uma API que pode ser usada
com o feature store, onde você pode alimentar
esses dados de streaming no feature
store e ele os processará.
Portanto, no Hood, o armazenamento de recursos terá um repositório
on-line desses recursos e também um repositório em lote.
Essa é a loja off-line no S3 para consultar recursos
da loja on-line e transmiti-los
de volta.
Há uma API Get Record que pode ser usada para isso.
Portanto, seu modelo pode transmitir esses
recursos usando a API Get Record -: Ou,
se você quiser fazer acesso em lote, é para isso que serve
o armazenamento off-line.
Portanto, o armazenamento de recursos do Stage Maker criará automaticamente
um catálogo de dados do Glue para esses dados armazenados no S3, e você poderá
fazer o que quiser com esses dados do S3.
Você pode usar ferramentas como o Athena ou o Data Wrangler.
Qualquer coisa que possa chegar ao S3 pode ser feita com
o armazenamento de recursos off-line.
Você também pode despejar dados diretamente nele, se desejar.
Assim, você não precisa transmitir dados para o armazenamento
de recursos do SageMaker.
Você pode simplesmente colocá-lo diretamente em sua loja off-line no S3
e fazer isso dessa forma também.
O que for melhor para você. O resultado final
é que o armazenamento de recursos do SageMaker funciona
com situações de streaming e também
com situações de lote baseadas na segurança do S3.
Tudo é criptografado automaticamente
em repouso e em trânsito.
E se você tiver uma chave mestra de cliente KMS, poderá usá-la com controle
de acesso refinado para armazenar os recursos o máximo possível
por meio do IAM, e também poderá protegê-la
com o link privado da AWS para garantir que ninguém possa acessá-la.
Isso não deveria acontecer.
