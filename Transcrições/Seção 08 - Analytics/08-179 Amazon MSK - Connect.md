chamado MSK Connect.
A ideia é que, no mundo do Kafka, você
tenha algo chamado Kafka Connect.
E o Kafka Connect é uma estrutura para pegar os dados do Kafka e colocá-los
em outro lugar.
Tudo isso para pegar dados de outro
lugar e colocá-los no Kafka.
Ao usar a estrutura do Kafka Connect no MSK, o que você pode fazer
é usar o MSK Connect, que fornecerá a você
trabalhadores gerenciados do Kafka Connect
no AWS com recursos de dimensionamento automático.
Isso significa que você pode implantar a infraestrutura
do Kafka Connect no MSK Connect e, em seguida,
implantar qualquer conector do Kafka Connect no MSK Connect
como um plug-in.
Assim, esses plug-ins podem, por exemplo,
enviar dados para o Amazon S3, Amazon Redshift, Amazon
OpenSearch, Debezium e assim por diante.
E aqui está um exemplo.
Você tem o cluster MSK em funcionamento.
Em seguida, você criará seus funcionários do MSK
Connect graças ao serviço MSK Connect.
E você implantará o plug-in,
que é o Amazon S3 Kafka Connector.
Em seguida, os funcionários
do Connect extrairão os dados do tópico de seu MSK Cluster.
E, como resultado, os dados
serão gravados no Amazon S3.
E não gerenciamos nenhuma infraestrutura.
Tudo isso é feito pelo MSK Connect e é apenas
uma configuração da nossa parte.
Portanto, há um preço, aqui está um exemplo.
Você paga 11 centavos de dólar por trabalhador e por hora.
E, é claro, quanto mais dados você tiver,
mais trabalhadores serão necessários.
Então é isso para o MSK Connect,
apenas uma introdução, caso você a veja no exame, espero
que tenha gostado.
E eu o verei na próxima palestra.
