o uso do Parameter Store.
Portanto, a melhor maneira de fazer
isso é digitar Parameter Store na barra de pesquisa, e você
pode clicar aqui.
É um recurso do Systems Manager.
Portanto, se você clicar em Parameter Store (Armazenamento de parâmetros), no lado esquerdo,
verá que, em Systems Manager (Gerenciador de sistemas), você tem,
em Application Tools (Ferramentas de aplicativos), o Parameter Store (Armazenamento de parâmetros),
e o que podemos fazer aqui é criar um novo parâmetro.
Especificamos tipos e valores e, em seguida,
podemos fazer referência aos parâmetros
nos comentários ou no código.
Então, vamos praticar o uso desse serviço.
Portanto, primeiro crio um parâmetro
e preciso inserir um nome para ele.
Portanto, o nome é o que você quiser.
Você não precisa seguir minha
orientação, mas eu gosto
de nomeá-lo assim: /my-app/dev/db-url, e isso me permitirá,
com essas quatro barras, organizá-los em uma
hierarquia.
Portanto, este é o meu aplicativo, este é o ambiente de desenvolvimento
e este é o nome do meu parâmetro no
ambiente de desenvolvimento.
Então, aqui, eu digo o URL do DB para o ambiente de desenvolvimento.
Isso é perfeito, e depois do Tier, temos duas opções.
Temos o Standard e o Advanced.
Portanto, usaremos uma camada padrão.
Podemos armazenar até 10.000 parâmetros padrão.
O valor máximo deles é de quatro kilobytes, e não podemos
compartilhá-lo com outras contas,
mas os parâmetros avançados podem ter 100.000 deles, podem ter oito kilobytes
e você pode compartilhá-los
com outras contas.
Em seguida, vamos escolher o tipo, que
pode ser String, StringList ou SecureString.
Portanto, aqui usaremos String, mas mais tarde
usaremos SecureString e, se precisar de uma
lista de strings, você
pode usar StringList, mas String aqui tem Data Type.
É um texto ou uma imagem do AWS EC2, porque você também
pode fazer referência a ARNs de imagem aqui, e aqui você só precisa
especificar o texto em um formato
específico.
Mas usaremos Text e, para a string, terei, por
exemplo, dev. banco de dados. stephantheteacher. com.
Este é apenas um exemplo.
Você não precisa colocar nada que seja um URL.
Você pode colocar o que
quiser nele, mas esse será o valor do meu parâmetro, este aqui.
Então, vamos criar esse parâmetro e, como
você pode ver, ele já foi criado.
Posso clicar nele e dar uma olhada.
Portanto, essa é a versão um desse parâmetro.
Podemos ver o histórico de versões aqui.
Portanto, se eu o alterar, é claro que poderei atualizá-lo,
mas terei acesso ao meu histórico de versões, o que é bom. Depois,
faremos o mesmo, mas adicionaremos mais
parâmetros, portanto, iremos para o Parameter
Store e copiaremos isso, e aqui o colocaremos
como db-password, portanto, vamos criá-lo.
Portanto, DB Password for Dev e, como você adivinhou,
desta vez teremos
um SecureString e, como se trata de uma senha,
vamos criptografá-la com uma chave KMS, para
que ela possa pertencer à minha conta
ou a outra conta.
Usaremos minha conta.
Você pode usar o KMS Key ID padrão gerenciado
pela AWS para o serviço SSM, que é este,
alias/aws/ssm, ou pode selecionar um que tenha sido
criado anteriormente.
Por exemplo, você pode ter criado, por exemplo, KMS, uma chave chamada Tutorial
ou o que quer que você queira criar.
Não é necessário e, portanto, se você o criou,
pode usá-lo aqui e aproveitá-lo.
Na verdade, você pode escolher
o que quiser, mas vamos escolher Tutorial
para este exemplo, pois não
importa, e precisamos colocar uma
senha, portanto, vou colocá-la como devpassword,
e agora ela será criptografada automaticamente pelo KMS.
Então, vamos criar esse parâmetro.
Como você pode ver agora, o tipo é um SecureString
e, se eu clicar nele, como você pode ver, o valor
será criptografado e ocultado e, se eu clicar em mostrar valor
descriptografado, ele verificará
se tenho permissão do KMS para usar a chave e, portanto,
descriptografará o valor para mim, o que é ótimo.
O que podemos fazer agora é criar rapidamente
os outros parâmetros para o Prod.
Então, em vez de aqui, tenho Prod e vou
chamá-lo de prod. stephantheteacher. com3306 e, em seguida, para
a senha, o mesmo.
Vou copiá-lo rapidamente e colocá-lo como produto.
Usaremos um SecureString, usaremos o Tutorial
e o colocaremos como prodpassword.
Agora, temos quatro parâmetros e todos eles estão disponíveis
no Parameter Store e são ordenados
por uma hierarquia.
Então, agora vamos tentar acessar esses parâmetros usando a CLI.
Portanto, vou abrir um CloudShell na parte superior
porque ele tem a CLI instalada do AWS
e já está configurado.
Portanto, o que vamos usar é um comando
chamado SSM Get Parameters.
Portanto, usaremos aws ssm get-parameters e, em seguida, você deverá fornecer
nomes, e os nomes correspondem
aos nomes dos parâmetros.
Assim, posso ter, por exemplo, meu dev/db-url,
bem como minha senha de dev, db-password.
Então, vamos pressionar Enter e, como você pode ver, agora obtenho um resultado
com meus dois parâmetros.
Portanto, temos este e aquele,
e você pode ver que, para o db-url, é um String, o valor
foi retornado como está, mas para o db-password,
é um SecureString e foi retornado como um
valor criptografado.
Portanto, para descriptografar esse valor, pressionarei Enter, Enter,
Enter e sair, q.
Preciso especificar um sinalizador,
e o sinalizador é chamado de with-decryption, portanto, ele
verificará adicionalmente se a política de segurança
do KMS é permitida em minha conta para descriptografar
esse parâmetro.
Portanto, como você pode ver agora, a db-password
ainda é uma SecureString, mas agora temos a devpassword como um valor
descriptografado graças a esse sinalizador com descriptografia.
Portanto, o CLA é muito
poderoso e pode ser usado em seus scripts.
Outro comando que gostaria de mostrar
a você é o Get Parameters by Path.
Então, você faz aws ssm get-parameters-by-path e precisa especificar
um caminho, e o caminho é o que você
quiser, portanto, como temos
uma hierarquia, temos my-app/dev, ele me fornecerá todos
os parâmetros nesse namespace e, como você pode ver,
temos novamente a dev db-password e a
dev db-url.
Mas agora você pode fazer algo mais, pode fazer, por exemplo,
o my-app como um todo e, como você pode
ver, não obtenho nada, mas
se eu usar o sinalizador e ele for um sinalizador
chamado Recursion, então ele será
recursivo, e você terá acesso a todos os parâmetros
recursivamente nesse namespace.
Portanto, temos acesso aos parâmetros do tipo dev e prod, o que
é ótimo, então agora temos nossos
quatro parâmetros.
E, por fim, se você quiser, é claro, também
pode usar with-decryption para descriptografar todos eles.
E é isso.
Então, vimos como o Parameter
Store estava funcionando, vimos a hierarquia, vimos a CLI
e começamos a mostrar a você o
poder de usar o Parameter Store.
Espero que tenham gostado
e nos veremos na próxima palestra.
