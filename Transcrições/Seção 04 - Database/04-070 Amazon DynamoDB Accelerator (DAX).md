Agora
O DAX é um cache em memória totalmente gerenciado,
altamente disponível e contínuo para o DynamoDB.
A ideia é que você armazene
em cache os dados mais
populares e, portanto, obtenha latência de microssegundos
para leituras e consultas em cache.
Ele não exige que você altere
nenhuma lógica do aplicativo e é compatível
com as APIs do DynamoDB existentes.
Basta criar um cluster DAX e pronto.
Agora, o DAX, o que ele resolve?
Ele resolve os problemas das teclas de atalho.
Portanto, se você estiver lendo uma chave muito específica
ou um item muito específico,
muitas vezes, poderá ter um estrangulamento em suas UCRs.
Mas se ele for armazenado em cache pelo DAX, então
você acabou de resolver esse problema.
Vamos dar um exemplo: o DynamoDB é feito de tabelas e nosso aplicativo
está tentando acessar essas tabelas.
Agora, nesse intervalo, vamos criar um cluster DAX,
que é composto de nós de cache, e precisamos
provisioná-los com antecedência.
Agora, o aplicativo interagirá diretamente
com o cluster DAX, e
o cluster DAX buscará os dados
das tabelas do DynamoDB.
Portanto, por padrão, isso significa que alguns dados serão
armazenados em cache e, se você
pensar em cache, precisará pensar em TTL.
Portanto, o TTL será de cinco minutos.
Portanto, por padrão, todos os dados do cache permanecerão
por cinco minutos em seu cluster DAX.
Agora, o cluster DAX é composto de
nós e, portanto, você precisa provisioná-los
e pode ter até 10 nós no cluster.
E é uma boa ideia estar em uma configuração do tipo Multi-AZ
para ter pelo menos três nós recomendados na produção.
Portanto, um em cada AZ.
E o DAX é totalmente seguro, portanto,
você tem criptografia em repouso.
Você tem aplicativo IAM, segurança VPC, integração
CloudTrail e assim por diante.
Portanto, lembre-se de que o DAX está aqui para ajudá-lo
a armazenar em cache os itens ou as consultas mais populares do DynamoDB.
Agora, a pergunta que temos
é: qual é a diferença entre o DynamoDB Accelerator,
ou seja, DAX e ElastiCache?
Bem, eles podem ser usados como uma combinação
e o exame pode testá-lo para descobrir se
é melhor usar o DynamoDB DAX ou se
você quer usar o ElastiCache.
Portanto, com o DAX, o que você
fará é ter um cache para objetos
individuais ou para suas consultas ou varreduras.
Isso é muito, muito útil,
e é o que chamo de tipos simples de consultas.
Portanto, seus objetos, suas consultas e suas varreduras.
Mas se você estiver fazendo algum tipo de aplicação lógica, você sabe
que está fazendo uma varredura e, em
seguida, faz a soma, filtra alguns
dados e assim por diante.
E você não quer fazer isso todas as vezes, porque
isso é computacionalmente caro.
O que você pode fazer é armazenar os resultados
do que o aplicativo acabou de fazer
no Amazon ElastiCache.
E recupere os dados do ElastiCache diretamente,
em vez de consultar novamente o DAX e executar novamente a agregação
no lado do cliente.
Portanto, essa pode
ser uma boa maneira de usar os dois juntos na arquitetura.
Está bem.
Então, vamos ver
como podemos criar um cluster DAX.
