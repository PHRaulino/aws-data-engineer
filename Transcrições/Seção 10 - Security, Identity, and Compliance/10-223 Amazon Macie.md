O Macie é um serviço de segurança e privacidade de dados
totalmente gerenciado que usará o aprendizado de máquina
e a correspondência de padrões para descobrir
e proteger seus dados confidenciais na AWS.
Mais especificamente, ele o alertará sobre dados confidenciais,
como informações de identificação pessoal,
que são chamadas de PII.
Assim, de forma muito simples, seus dados de PII estarão em seus buckets
do S3 e serão analisados pela Macie,
que descobrirá quais dados podem ser classificados como PII.
Em seguida, você será notificado
por meio do EventBridge sobre as descobertas.
Em seguida, você pode ter integrações em um tópico do SNS, funções
Lambda e assim por diante.
Portanto, o Macie, nesse caso, será usado para
localizar os dados confidenciais em seus buckets do S3 e
essa é a única coisa que ele fará.
Basta um clique para ativá-lo.
Basta especificar os buckets do S3 que você
deseja ter e pronto.
Então é isso para esta palestra, muito, muito curta,
mas é o suficiente sobre a Macie.
Espero que tenham gostado e nos veremos na próxima palestra.
