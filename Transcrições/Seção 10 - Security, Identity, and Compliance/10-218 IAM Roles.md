Então, temos que
IAM, que se chama IAM Roles.
Portanto, alguns serviços da AWS que lançaremos
ao longo deste curso precisarão executar
ações em nosso nome, em nossa conta, certo?
E para que eles realizem essas ações, eles
são como os usuários,
eles precisarão de algum tipo de permissão.
Portanto, precisamos atribuir permissões aos serviços
do AWS e, para isso,
vamos criar o que chamamos de função IAM.
Portanto, essas funções de IAM serão como
um usuário, mas não devem ser usadas por pessoas
físicas, mas sim por serviços da AWS.
Então, o que isso significa?
É um pouco confuso.
Assim, por exemplo,
vamos criar uma instância EC2 ao
longo deste curso.
Uma instância do EC2 é como um servidor virtual,
e veremos isso na próxima seção.
Mas, para que essa instância do EC2 possa
executar algumas ações no AWS e, para isso, precisamos
conceder permissões à nossa instância do EC2.
Para isso, criaremos uma função IAM e, juntos,
eles formarão uma entidade.
E, juntos, quando a instância EC2 estiver
tentando acessar algumas informações do AWS,
ela usará a função IAM.
E se a permissão atribuída à função IAM estiver correta, teremos
acesso à chamada que estamos tentando
fazer.
Portanto, algumas funções comuns incluem
o que acabei de mostrar a você, funções de instância EC2, mas
também outras coisas que executam ações em relação à AWS que veremos
neste curso.
Por exemplo, funções de função Lambda ou CloudFormation.
Portanto, sei que se trata de uma revisão de alto nível.
Na próxima aula, criaremos uma função,
mas não a usaremos até a próxima seção, mas vamos em frente
e criar uma função.
Eu o verei na próxima palestra.
