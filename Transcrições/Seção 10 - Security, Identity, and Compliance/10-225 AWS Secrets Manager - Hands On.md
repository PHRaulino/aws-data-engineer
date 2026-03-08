Então, agora
Portanto, como podemos
ver, é fácil rotacionar, gerenciar e recuperar segredos durante
todo o seu ciclo de vida.
Portanto, ele é semelhante ao armazenamento
de parâmetros do SSM porque você pode armazenar
coisas secretas, mas será diferente
dele porque, embora você tenha rotação, gerenciamento
e integrações rigorosas com bancos de dados como
MySQL, PostgreSQL, Amazon Aurora, RDS e assim por diante.
Portanto, o preço é que você tem uma avaliação gratuita de 30 dias disponível
e, depois, pagará US$ 0. 40 por segredo, por mês,
e depois $0. 05 por 10.000 chamadas de API.
Portanto, se você espera permanecer no nível gratuito,
basta criar um segredo e excluí-lo.
Então, vamos em frente e armazenar um novo segredo,
e podemos escolher um tipo de segredo.
Agora, com o tempo,
é bem possível que isso aumente em termos
de capacidade de integrações, mas temos
o Amazon RDS, o Amazon DocumentDB, o Amazon Redshift,
outros bancos de dados ou outros tipos de segredos.
Portanto, se você estiver no Amazon RDS, como pode ver, ele solicitará
o nome de usuário e a senha, e assim por diante.
E se você for, por exemplo,
para outros tipos de segredos,
aqui podemos armazenar o que quisermos.
Assim, por exemplo, posso dizer MySecretKey
e MyVerySecretValue, e esse seria um segredo
armazenado aqui.
E outra poderia ser, por exemplo, API_KEY, que também
seria como uma chave secreta de API, então você
digitaria algum texto aqui.
Portanto, você pode inseri-lo por meio dessa
interface do usuário ou digitá-lo em texto simples e ter um documento adjacente
que pode ser editado.
Para editar os valores das chaves, essa
é apenas uma maneira diferente de especificar seus segredos.
Portanto, isso será mantido em segredo para que somente as
pessoas com as permissões corretas do IAM possam acessar esses segredos.
Em seguida, especificamos uma chave de criptografia.
Portanto, temos a chave padrão,
mas você pode usar sua própria chave KMS, se quiser.
Eu clico em "next".
Em seguida, precisamos nomear nosso segredo.
Então, prod/my-secret, por exemplo, e uma
descrição, mas não preciso dela.
Permissão de recursos,
então queremos ter uma política que restrinja
quem pode acessar o segredo?
E isso poderia ser feito em todas as contas
da AWS graças a essa política de recursos aqui, e você teria um formulário
adjacente.
Portanto, é semelhante a uma política de bucket do S3.
E então você tem a opção de
replicar o segredo entre as regiões.
E isso é bom se você quiser ter configurações de várias regiões, como aplicativos
de várias regiões ou bancos de dados de várias regiões.
E aqui podemos
dizer: "Ok, quero replicar
isso no us-west-2 usando essa chave de criptografia
aqui e também no AP Southeast-1 e assim por diante.
Portanto, não
vou fazer isso, mas seria assim que você replicaria seus segredos.
Então, eu clico em Next.
Então você deseja rotacionar automaticamente nossos
segredos, sim ou não.
E quando quisermos girá-lo, e se habilitarmos
a rotação, precisaremos especificar
uma função de rotação.
Essa é uma função Lambda
que executará essa rotação.
Portanto, por enquanto, desative-o.
E então vamos dar uma olhada.
Portanto, temos um segredo bem aqui.
Ele é replicado no us-west-2.
E aqui está um código se quisermos invocar e obter
esses segredos de nossos clientes.
Portanto, não vou prosseguir com
a criação, mas, como você pode ver, isso armazenaria
um segredo e, em seguida, usaria esse código
para recuperar em seu código os segredos corretos.
Portanto, vamos cancelar isso.
Outro tipo de segredo que você
pode ter é uma credencial para um banco de dados Amazon RDS.
Assim, você criaria um nome de usuário e uma senha e,
em seguida, especificaria um banco de dados.
E o mais legal é
que, graças à integração
entre o RDS e o Secrets Manager, esse nome
de usuário e essa senha seriam
usados para fazer login no banco de dados.
E se você quiser girá-lo, o banco
de dados também será atualizado automaticamente.
Portanto, aqui você deve inseri-lo.
Em seguida, você também configuraria
os segredos se quisesse ter,
por exemplo, algum tipo de replicação em várias regiões.
Rotação também, se você quiser revisá-la e pronto.
Então, é isso para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
