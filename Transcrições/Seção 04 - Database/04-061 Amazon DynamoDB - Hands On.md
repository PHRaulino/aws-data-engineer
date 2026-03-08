Agora, vamos dar uma olhada no serviço DynamoDB.
E o serviço DynamoDB nos permitirá criar tabelas.
Como você pode ver, podemos criar tabelas, não bancos de dados,
porque o banco de dados já foi criado para nós e essa é uma oferta
sem servidor.
Então, vamos em frente e criamos as tabelas.
Portanto, o nome da tabela precisa ter um
nome, então digitaremos "Users". Em seguida, temos que definir
uma chave de partição e, opcionalmente,
uma chave de classificação.
Portanto, para a chave de partição, usarei "user_ID"
e, em seguida, podemos alterar o tipo,
que pode ser binário, numérico ou string,
mas deixarei como string.
E então podemos usar uma chave de classificação,
mas mostrarei isso mais tarde.
Portanto, no momento, vamos deixá-lo vazio.
Agora, o início rápido permite que você comece
com as configurações padrão e define algumas configurações para você.
Ou você pode personalizar as configurações,
sobre configurações personalizadas.
Portanto, a primeira coisa é a classe da mesa.
Portanto, é possível usar o padrão DynamoDB,
que é uma classe de tabela de uso
geral recomendada para a maioria dos casos de uso.
Mas se você tiver dados que ficarão
parados por um longo tempo e não tiver
muitas leituras ou gravações, a IA padrão
do DynamoDB dirá que os dados são acessados com
pouca frequência e fornecerá algumas
otimizações de custo.
Mas, neste momento, usaremos um
padrão que é o padrão do DynamoDB.
Calculadora de capacidade, veremos isso
mais tarde porque precisamos entender como calcular
a capacidade no DynamoDB, mas, por enquanto, não fazemos nada aqui.
E, em seguida, dois modos de capacidade de leitura e gravação sob demanda ou provisionada,
sendo que a provisionada está dentro da camada gratuita.
Novamente, teremos uma longa discussão sobre esses modos
mais tarde, mas usaremos o provisionamento porque
ele está dentro do nível gratuito.
Em seguida, temos que configurar a capacidade de leitura e gravação,
e vou desativar o dimensionamento automático para ambos.
Portanto, fornecemos apenas uma capacidade fixa de leitura e gravação.
E temos duas unidades de capacidade na camada gratuita,
portanto, vou configurar, temos 10, desculpe,
na camada gratuita.
Portanto, vou configurar
duas unidades de capacidade de provisionamento para
leituras e duas para gravações.
E veremos como eles evoluirão com o tempo.
Por enquanto, vamos criar um índice secundário,
pois isso é algo que será avançado mais adiante
neste curso.
E aqui temos o custo estimado para essa tabela,
que é de US$ 1. 32 por mês.
Agora, como estamos no nível gratuito,
você pode desconsiderar esse número, certo?
Mas se você não estiver no nível
gratuito, esse seria o valor mensal dessa tabela.
Em seguida, criptografaremos os dados
em repouso usando a chave do DynamoDB.
Vamos deixar assim, mas temos outras opções.
E quando estiver pronto, clique em criar tabela.
Pronto, minha tabela já foi criada.
Posso clicar nele e removerei o painel esquerdo e, como podemos ver, obteremos
muitas informações sobre nossa tabela.
Então, vamos às configurações da nossa mesa.
Portanto, qual é a chave de partição, a chave de classificação,
o modo de capacidade e há alguma replicação, data de criação e assim
por diante.
Portanto, muitas informações e, para nós, as coisas
importantes estarão relacionadas aos itens.
Portanto, se eu rolar a tela para baixo, há a opção Exibir itens.
Ou, se eu for para o lado direito, há também a opção View Items.
Agora, como podemos ver, posso examinar ou consultar
minha tabela, mas o que vou fazer é criar um item.
Portanto, nesse item de criação, posso escolher um ID de usuário e precisamos
definir as chaves de partição.
Por exemplo, John123.
E esse é apenas um ID de usuário, aleatório,
que pode ser inserido como você quiser.
E então podemos adicionar atributos para John123.
Portanto, podemos adicionar
a força, por exemplo, e a força será "first_name",
e o valor será bem, John.
E se tivermos uma string e ela for "last_name", poderemos
ter Doe, John Doe.
E, como podemos ver,
podemos adicionar muitos atributos que quisermos a esses tipos.
Então, estamos prontos para começar, vamos apenas criar um item.
E, como podemos ver, isso pode
ser feito por meio de um formulário ou de um documento adjacente.
Portanto, vamos mantê-lo como um formulário e criar esse item.
Portanto, agora esse item, John Doe, está aparecendo
na minha tabela, como podemos ver, temos o ID do usuário, o nome e o sobrenome.
Portanto, o que podemos fazer é começar a adicionar um segundo item.
Então, vamos criar um segundo item.
E se eu mantiver John123 como meu valor e disser apenas
Johnny como meu primeiro nome, por exemplo, só para mostrar algo, se eu fizer isso e clicar
em criar item, terei um problema porque,
bem, estou usando o mesmo ID de usuário de antes e ele precisa
ser exclusivo quando tenho apenas uma
chave de partição.
Portanto, isso não funciona.
Então, o que posso fazer é criar Alice456 e o primeiro
nome será Alice.
Não sabemos o sobrenome dela,
portanto não vamos especificar
o sobrenome, mas sabemos a idade dela e ela tem 41 anos.
Agora, se eu tentar criar esse
item, algo muito interessante acontecerá.
Portanto, como você pode ver, a solicitação foi bem-sucedida.
Portanto, em um banco de dados SQL RDS, você teria tido um problema ao dizer
que a coluna não estava definida, que alguns valores
são nulos, etc., mas aqui conseguimos fazer com que
João tivesse um nome e um sobrenome e Alice tivesse
apenas uma idade e um nome.
Portanto, no DynamoDB,
não há problema algum em adicionar atributos ao longo
do tempo, certo? A única coisa que precisa ser não nula
é a ID do usuário, mas, como podemos ver, ela é nula por padrão.
Portanto, John tem uma idade
nula e Alice tem um sobrenome nulo, mas tudo bem.
Portanto, esse é o poder do DynamoDB,
também um risco, mas também o poder.
Você pode adicionar atributos ao longo
do tempo sem afetar seus dados anteriores.
E não há problema algum nisso, ok?
Você não pode definir no DynamoDB uma restrição
dessa coluna que não seja nula, ela simplesmente
não existe, certo?
Portanto, temos nossa primeira tabela
sendo criada, mas é muito fácil continuar criando tabelas.
Então, volto ao DynamoDB e clico em "create table" (criar
tabela). Podemos criar uma segunda tabela chamada "UsersPosts" (custos dos usuários), certo?
Ou "UserPosts. Está bem.
a chave de partição será novamente o ID do usuário, mas agora teremos
Agora,
uma chave de classificação que é post TS para carimbo de data/hora,
novamente, do tipo string, binário ou número.
E o que queremos criar aqui é
uma tabela de dados, que terá a postagem dos usuários.
Então, novamente, personalizaremos as configurações
e usaremos provisões, usaremos
apenas "off" (desligado), e teremos dois e dois, e então
rolaremos para baixo e criaremos essa segunda tabela.
Portanto, como podemos ver agora, tenho duas tabelas em meu banco de dados.
E, mais uma vez, não é necessário dizer o que está acontecendo com a tabela,
qual é o banco de dados subjacente,
na verdade, você pode criar quantas tabelas
quiser dentro do seu banco de dados DynamoDB, entre aspas, o que é feito
no nível da região.
Então, agora vamos para UserPosts, e podemos ver
que há uma chave de partição e uma chave de classificação
sendo definidas.
Portanto, se eu for para a visualização
de itens e criar um item, precisaremos especificar
um ID de usuário, por exemplo, John123 e um carimbo de
data/hora de postagem.
Assim, por exemplo, 2021,10, 09.
E então você se certifica de que esse é o registro de data
e hora correto, mas esperamos que seja.
TS e, em seguida, uma hora, ou seja, 123409Z.
Está bem. Em seguida, precisamos adicionar algum conteúdo à nossa postagem.
Então, vou dizer o
conteúdo e dizer: "Olá mundo, este é meu primeiro blog. Muito bem, excelente.
Agora vamos criar esse item.
E, como você pode ver, agora temos o ID de usuário John
e a postagem com o carimbo de data/hora this e alguns conteúdos.
Então, o que acontece se criarmos um segundo item no qual podemos
manter John123 como meu ID de usuário e, para o carimbo de data/hora
da postagem, teremos apenas 2021, talvez algo um pouco posterior.
Portanto, 11, 04T e, novamente, apenas um registro de data e hora aleatório.
Está bem. E vamos adicionar um novo conteúdo
e dizer: "Segunda postagem! Ok, e crie esse
item.
Portanto, como podemos ver, isso funcionou.
Portanto, embora tenhamos o mesmo ID de usuário,
como o carimbo de data/hora da postagem era diferente,
conseguimos inserir esses dados na minha tabela.
Portanto, a exclusividade deve estar
no ID do usuário e no carimbo de data/hora da postagem como uma combinação.
Isso significa que os dados são particionados por ID de usuário.
Portanto, é por isso que o John
é clicável, pois podemos consultar e pesquisar John123 como meu ID de usuário.
E então podemos classificar os dados por carimbo de data/hora de postagem, certo?
Por isso, ela é chamada de chave de classificação.
Portanto, isso é muito, muito, muito útil.
E, como podemos ver, se quisermos criar um último item para Alice456,
novamente você precisará inserir um carimbo de data/hora
da postagem e algum conteúdo e estará
pronto para começar.
E é por isso que é muito importante
escolher uma chave de partição realmente boa nesses momentos, porque
se você escolher uma chave
de partição que continua voltando, então se John123
for o único usuário que publica e você tiver 10.000 publicações,
os dados serão fortemente inclinados para
John123.
Portanto, é preciso estar ciente de algo, certo?
Então é isso para esta palestra.
Espero que você tenha gostado.
E eu o verei na próxima palestra.
