e o nome indica que ele é, na verdade,
um banco de dados de séries temporais.
Portanto, ele é totalmente gerenciado, rápido,
dimensionável e sem servidor.
Então, o que é uma série temporal?
Bem, é um conjunto de pontos que têm um tempo
incluído.
Por exemplo, aqui está um gráfico por ano.
Portanto, essa é uma série temporal.
Agora, com o Timestream, é possível ajustar
automaticamente o banco de dados para cima e para baixo para dimensionar a capacidade
e armazenar e analisar trilhões de eventos por dia.
A ideia é que, se você tiver um banco de dados de séries temporais,
ele será muito mais rápido e muito mais barato do que usar bancos
de dados relacionais para dados de séries temporais.
Daí a especificidade de ter um banco de dados de séries temporais.
Você pode fazer consultas agendadas.
É possível ter registros com várias medidas
e há compatibilidade total com SQL.
Os dados recentes serão mantidos na memória.
E, em seguida, os dados históricos são mantidos
em uma camada de armazenamento com custo otimizado.
Além disso, você tem a função de análise de séries temporais
para ajudá-lo a analisar seus dados e encontrar padrões
quase em tempo real.
Esse banco de dados, assim como todos os bancos de dados no AWS,
oferece suporte à criptografia em trânsito e em repouso.
Portanto, os casos de uso do Timestream seriam um aplicativo
de IoT, aplicativos operacionais,
análises em tempo real, mas tudo relacionado
a um banco de dados de séries temporais.
Agora, em termos de arquitetura, o Timestream está aqui
e pode receber dados do AWS IoT, ou seja, da Internet das coisas.
Os fluxos de dados do Kinesis por meio do Lambda também podem
receber dados.
Prometheus, Telegraf, existem integrações para isso.
O Kinesis Data Streams e o Kinesis
Data Analytics for Apache Flink também
podem receber dados no Amazon Timestream e no Amazon
MSK por meio do mesmo processo.
E em termos do que pode ser conectado ao Timestream,
onde podemos criar painéis usando o Amazon QuickSight.
Podemos fazer aprendizado de máquina usando o Amazon SageMaker.
Podemos usar o Grafana ou, como há uma conexão
JDBC padrão em seu banco de dados, qualquer
aplicativo compatível com JDBC e SQL
pode aproveitar o Amazon Timestream.
Então é isso.
Acho que, para o exame, você só precisa se
lembrar do que é o Timestream em um nível
elevado, mas também quero lhe dar um pouco mais de detalhes.
Então é isso para esta palestra.
Espero que tenham gostado
e nos veremos na próxima palestra.
