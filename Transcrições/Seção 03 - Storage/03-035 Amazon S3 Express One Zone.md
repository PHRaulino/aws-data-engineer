Então, aqui está mais uma aula sobre armazenamento,
para ela porque é um pouco diferente das outras.
Portanto, a classe de armazenamento S3 Express One Zone é de alto desempenho,
mas para um tipo de classe de armazenamento
de zona de disponibilidade única.
O que isso significa?
Isso significa que seus objetos
são armazenados não no bucket padrão do S3,
mas no que é chamado de bucket de diretório, que
é um tipo especial de bucket do S3.
Mas esse bucket, em vez de ser distribuído
em várias zonas de disponibilidade, ficará
em uma única zona de disponibilidade, e você pode
escolher em qual delas deseja que ele fique.
Portanto, é um tipo diferente
de balde, e é por isso que também há um tipo diferente
de classe de armazenamento.
Portanto, trata-se de um caso de uso muito específico,
mas a ideia é que, como você está em um único AZ, poderá
lidar com centenas de milhares de
solicitações por segundo com latência
de milissegundos de um dígito, ou seja, um desempenho
muito alto.
Você obtém cerca de 10 vezes o desempenho do padrão
S3 com um custo cerca de 50% menor.
Portanto, a durabilidade é boa, mas a disponibilidade é obviamente menor, porque agora, em
vez de três zonas de disponibilidade com alguma replicação,
você tem apenas uma zona de disponibilidade.
E, é claro, se houver um problema nesse AZ,
você será diretamente afetado.
Portanto, a ideia de usar o S3 Express One Zone é que você poderá
co-localizar seus recursos de armazenamento e computação
na mesma zona de disponibilidade e, portanto, reduzir
a latência e talvez até mesmo
reduzir seu custo de rede.
Portanto, os casos de uso são para aplicativos sensíveis à
latência, para aplicativos com uso intensivo de dados, para treinamento
de IA e ML, modelagem financeira,
processamento de mídia e computação
de alto desempenho, e é melhor integrado,
por exemplo, com o SageMaker Model Training, Athena, EMR, Glue, todos esses
tipos de serviços de dados.
Muito bem, então é isso para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
