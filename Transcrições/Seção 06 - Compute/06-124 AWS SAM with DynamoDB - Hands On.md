fica quando você também tem uma tabela DynamoDB.
Então, faremos o sam init e, em seguida, usaremos
novamente os modelos de início rápido e,
desta vez, usaremos uma API sem servidor, portanto,
a número sete neste caso.
Em seguida, usaremos o nodejs22.
E então não queremos o raio X, não queremos
isso, não queremos aquilo.
E então chamarei este de sam-app-dynamodb.
Certo, então aqui o que temos é um diretório, porque sam-app-dynamo, oh,
eu cometi um erro de digitação, mas não importa,
está tudo bem.
E nele, novamente, se olharmos os
arquivos, encontraremos. -print, temos a mesma estrutura de antes,
mas agora temos alguns códigos-fonte, como os códigos-fonte do JavaScript.
Eles foram criados para
o JSON, portanto, você não precisa se lembrar deles.
O que é importante, novamente, é o modelo do arquivo
yaml que quero mostrar a você.
Então, se eu fizer um modelo de gato. yaml, como você pode ver, esse
é um modelo mais completo, porque essa é uma API sem servidor
completa, mas vamos dar uma
olhada.
Novamente, temos essa transformação sem servidor que
é muito importante para o SAM e, em
seguida, temos recursos.
Portanto, temos várias funções.
Temos o getAllItemsFunctions,
que é uma função sem servidor, e temos
a origem, o tempo de execução, a memória, a política, o que é
muito importante aqui.
É uma política muito simples
que se tornou possível graças à estrutura SAM.
Portanto, aqui temos uma política bruta do DynamoDB em uma
referência ao nome da tabela, e é isso, é tudo o que precisamos
para criar uma política IAM com a estrutura
SAM, o que a torna muito fácil em comparação
com o CloudFormation bruto, bem como os eventos aos quais ela deve responder.
Portanto, isso deve ser um GET no caminho raiz como uma API.
Novamente, uma maneira muito fácil de definir uma API.
Em seguida, temos outra função sem servidor, outro manipulador,
novamente, outra política e outro caminho de API.
Mais uma vez, é muito fácil defini-lo, graças a isso.
Temos uma terceira função. Isso é para ser colocado desta vez.
Então, você vê que o método é POST.
E, em seguida, temos a tabela de amostra, que
é uma tabela simples, que, nos bastidores,
é convertida em uma tabela do DynamoDB.
Temos a chave primária e, em seguida, fornecemos a taxa de transferência
para a unidade de capacidade de leitura e gravação como dois.
E é isso, é tudo o que precisamos
fazer para implantar uma API completa no AWS com a estrutura SAM que é apoiada
por uma tabela do DynamoDB.
Portanto, esses exemplos
são ótimos, porque realmente permitem
que você veja e mostre o poder da CLI do SAM.
Se quiser se divertir, você pode implantá-lo,
mas, se o implantar, certifique-se de excluí-lo depois,
fazendo sam delete.
Mas você pode se divertir e implementá-lo se quiser,
não é necessário mostrar a etapa, pois você já sabe disso.
É isso e, infelizmente, não posso executar esse recurso
localmente no Cloud Shell,
mas o SAM tem capacidade local.
Mas uma coisa que eu poderia lhe mostrar é que você tem eventos aqui,
e nesse evento temos eventos de amostra.
Portanto, posso copiar um, e esses eventos são eventos de amostra.
E, em seguida, podemos usar o comando sam local invoke, mas isso não funcionará
no Cloud Shell porque não tenho
os itens necessários instalados.
Preciso do Docker e assim por diante
para realmente executar esses eventos e testá-los.
Portanto, se você quiser, em
seu tempo livre, brincar com esse recurso, o que você
pode fazer é ler o leia-me. md, e lá você encontrará
em algum lugar aqui, aqui, essas duas funções para invocar o aplicativo
localmente, para que você possa
executá-lo localmente e, em seguida,
invocar a função de colocar
item com esse evento específico.
Em seguida, você pode invocar a função getAllItemsFunction
com esses eventos específicos para testar
sua função localmente sem nem
mesmo implantá-la no AWS.
Você pode até mesmo iniciar um gateway de API local
diretamente no seu computador usando o sam local start-api,
e pronto, você tem algo no seu computador.
Isso permite que você faça iterações muito rapidamente
em seu computador e, quando terminar, faça o upload para o AWS.
Então é isso para esta palestra, na qual quero mostrar a você como
configurar o DynamoDB e como executar as coisas localmente.
Espero que tenham gostado e nos veremos na próxima palestra.
