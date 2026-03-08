UDFs são algo que você precisa
conhecer e são uma funcionalidade incrível.
Isso permite que você use funções no AWS Lambda
dentro de suas consultas SQL no Redshift.
E isso é poderoso, certo?
Porque as funções Lambda podem ser escritas em praticamente qualquer
linguagem que você possa imaginar.
E eles podem fazer praticamente qualquer coisa que você possa imaginar.
Assim, você poderia ter uma função Lambda que
chamasse outros serviços, talvez como um serviço de IA, certo?
Ele pode acessar outros sistemas que podem ser externos.
Ele também pode se integrar aos serviços de localização.
Esses são apenas alguns exemplos do que você
pode fazer com uma função do AWS Lambda que é acessada
de dentro da sua consulta SQL.
Para usá-las, basta criar uma função externa para
registrar as UDFs do Lambda
que você usa em suas consultas.
E na própria tabela do Redshift, você precisa
conceder o uso da LANGUAGE EXFUNC para que isso funcione
e para que tudo tenha
as permissões corretas para conversar
com o Lambda.
Um exemplo de como isso pode ser.
Vamos imaginar que temos um UDF Lambda_multiply que
definimos.
Portanto, poderíamos dizer
select a, b from t1 where Lambda_multiply a, b equals 64.
Portanto, isso poderia ser usado
para dizer: "Quero selecionar todas as linhas da
minha tabela em que o produto das colunas a e b seja igual a 64".
E esse é um exemplo talvez muito bobo de pensar demais
nas coisas.
Mas, nesse caso, chamaríamos o AWS Lambda para realizar
essa multiplicação.
Obviamente, coisas muito mais complicadas poderiam ser feitas lá.
Tudo o que o AWS Lambda pode fazer pode ser feito
dentro dessa função Lambda_multiply.
Portanto, a ideia aqui é que estamos vinculando
o Lambda ao Redshift por meio de UDFs muito bem elaboradas.
Agora, para realmente registrar
essa função, veja como seria a sintaxe.
Portanto, este é um exemplo diferente.
Vamos criar aqui uma UDF exfunc_some que pega dois números
inteiros e os soma, presumivelmente.
Portanto, a sintaxe para definir essa UDF exfunk_sum seria criar
uma função externa, o nome dessa função
e, em seguida, uma lista dos parâmetros
que ela espera.
O que ele retorna, nesse caso, é outro número inteiro.
Portanto, ele recebe dois números inteiros e retorna um número inteiro.
Essa é, provavelmente, a soma de todos eles.
Volatile Lambda e, em seguida, o nome da função Lambda
que estamos chamando.
E, por fim, passamos a função IAM associada a essa
função Lambda para dar a ela
as permissões necessárias para
acessar o que precisa acessar.
Um pouco mais de detalhes sobre essa função de IAM.
Portanto, há uma política de IAM de função do AWS Lambda que você pode usar para conceder
permissões ao Lambda na função de IAM de seus clusters.
Ou você pode criar sua própria apólice.
Apenas certifique-se de que está permitindo a função de invocação
do Lambda como parte dessa política.
Portanto, você precisa criar uma função com essa política
e, em seguida, passá-la por meio desse parâmetro em
seu comando de criação de função externa,
como vimos anteriormente.
Também é possível invocar funções em outras contas na mesma
região usando o encadeamento de rolos do IAM dessa forma.
Portanto, você pode usar o Lambda UDF de outra pessoa usando o encadeamento
de rolos.
Então, como tudo isso funciona por trás do capô?
O que acontece quando ele realmente vai para o Lambda?
Portanto, o Redshift estará se comunicando com sua função
Lambda usando dados JSON.
Portanto, eis o que sua função Lambda pode ver ao entrar.
Ele verá um ID de solicitação, o cluster de onde veio, o usuário
do banco de dados de onde veio no Redshift, o nome da
função externa e, em seguida, um ID de consulta.
E, finalmente, o número de registros
que ele deseja que você calcule.
Portanto, nesse caso, estou dizendo que quero
que você descubra quatro coisas.
Aqui está a lista de argumentos para cada uma dessas quatro coisas.
Em seguida, sua função Lambda faz algo com isso e
fornece uma resposta.
Essa resposta pode ser parecida com a seguinte.
Ele indicará sucesso, verdadeiro ou falso.
Se houver uma mensagem de erro, você também poderá especificá-la.
Vou dizer que estou devolvendo quatro registros
aqui que você pediu.
E aqui estão os resultados.
Uma lista dos resultados de todos os quatro registros
que você solicitou.
Portanto, bastante simples, certo?
Basicamente, o Redshift diz:
"Ok, bem, estou chamando o Lambda.
Aqui está o Lambda, aqui estão os parâmetros que você deseja.
Dê-me uma resposta e eu a incluirei
em minha resposta no SQL. Portanto, isso é Redshift,
Lambda, UDFs, funções definidas pelo usuário que
chamam o Lambda.
Em poucas palavras. Funcionalidade muito legal.
