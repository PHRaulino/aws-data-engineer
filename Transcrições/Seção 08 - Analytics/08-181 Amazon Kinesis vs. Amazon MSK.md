você terá que escolher o Kinesis
Data Streams em vez do Amazon MSK.
Porque a AWS gosta que você use seus produtos.
Mas é importante que, talvez em um ou dois casos, você
tenha que dizer que o Amazon MSK é a inserção correta.
E para que você saiba disso, é necessário conhecer
as diferenças entre o Kinesis Data Streams
e o Amazon MSK e as principais.
Portanto, no Kinesis Data Streams,
há um limite rígido de um megabyte para o tamanho da mensagem
e você não pode ultrapassá-lo.
Portanto, no Amazon MSK, é um megabyte por padrão, mas você pode configurar
para contratar, por exemplo, 10 megabytes.
E isso será uma grande diferença.
Portanto, se você vir uma mensagem grande
no exame, isso excluirá todos os casos em que os fluxos
de dados respondem ou o Firehose responde e vai direto
para o Amazon MSK.
Em vez de fluxos, ele
é chamado de Data Streams with Shards e, no Amazon MSK, é chamado
de Kafka Topics with Partitions, mas são
bastante semelhantes. Em fluxos de dados, no entanto, você
pode fazer a divisão e a fusão de fragmentos.
Portanto, aumente ou diminua a taxa de transferência
de seu fluxo de dados.
Já no Amazon MSK, o dimensionamento é um pouco
mais difícil e você só pode adicionar
partições a um tópico. Não é possível remover partições de um tópico.
Em termos de criptografia, o Kinesis Data Streams
tem a criptografia TLS In-flight ativada por padrão.
Já no Amazon MSK, você tem a opção
de escolher enviar os dados em PLAINTEXT.
Portanto, não há criptografia nem TLS In-flight Encryption também.
Você obtém a criptografia KMS At-rest para ambos os serviços.
E, em termos de segurança, você tem políticas de IAM
para autorização e autenticação no lado do
Kinesis Data Stream e, para segurança no Amazon MSK, você pode
obter o Mutual TLS para autenticação e ACLs do Kafka para autorização,
que é a combinação número um ou SASL/SCRAM para autenticação
e ACLs do Kafka para autorização.
é o número dois, ou o controle de acesso
Esse
IAM para fazer a autorização e a autenticação no MSK também.
Portanto, você precisa escolher uma dessas opções.
Espero que ela o ajude a ganhar
alguns pontos valiosos no exame.
E eu o verei na próxima palestra.
