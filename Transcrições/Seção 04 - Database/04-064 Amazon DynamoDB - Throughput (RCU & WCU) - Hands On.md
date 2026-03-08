Então,
vamos dar uma olhada em como podemos definir a RCU e a WCU de nossas tabelas.
Portanto, se pegarmos a tabela do usuário, por exemplo, e formos
para o lado direito e fizermos configurações
adicionais, teremos a capacidade
de leitura/gravação e poderemos editá-la.
Portanto, foi isso que definimos no momento da criação da tabela.
Mas o interessante do DynamoDB é que
podemos alternar entre os modos de capacidade,
se necessário, e também
podemos alterá-los ao longo do tempo.
Portanto, vamos usar o modo de capacidade mais simples
no momento, que é o On-demand.
E esse é um faturamento simplificado para
pagar pelas leituras e gravações reais do seu aplicativo.
Mas isso é duas ou três
vezes mais caro do que o provisionado.
Obviamente, isso ocorre quando
você tem um tipo de carga de trabalho muito incomum e imprevisível, ou
talvez isso ocorra em seus ambientes de desenvolvimento,
e vamos considerar que você não esteja usando
em um dia, durante uma hora, você esteja usando
muito a tabela.
Portanto, esse é um ótimo modo de capacidade,
pois ele realmente o capacita para o que você está
usando, o que é incrível.
Agora, há o modo de capacidade provisionada,
e foi nesse modo que passamos a maior parte do tempo
para entender e computar as leituras e gravações.
Portanto, vamos acessar a calculadora de capacidade.
Portanto, como podemos ver
aqui, você pode especificar o tamanho médio do item, por exemplo,
seis kilobytes, quantas leituras por segundo você deseja,
talvez três leituras por segundo e duas gravações por segundo.
O tipo de leitura que você deseja
ter é consistente e fortemente consistente, existe a transacional,
mas definirei isso
um pouco mais adiante.
Eu não queria sobrecarregá-lo neste momento.
Portanto, eventualmente ou fortemente consistente e, em seguida, para a
consistência de gravação, o mesmo
padrão ou transacional, mas, novamente,
tradicional, veremos isso um pouco mais tarde.
E, como podemos ver, com base no que
escolhi, ele me fornece a RCU e a WCU, bem como
o custo estimado que terei para minha mesa.
Portanto, essa é uma calculadora
bastante útil, e eu sugiro que você pratique um pouco
com essas configurações e tente adivinhar corretamente
qual é a RCU e a WCU para essa tabela, pois isso
é algo que o exame perguntará.
Legal.
Agora, vamos dar uma olhada na capacidade da tabela.
Portanto, é óbvio que podemos ter o escalonamento automático
desativado e o escalonamento automático desativado para leitura
e gravação e, portanto, você precisa provisionar unidades
de capacidade e elas não mudarão
com o tempo, a menos que você as altere manualmente.
Mas você também pode configurar o dimensionamento automático.
E o dimensionamento automático
é muito legal, porque estamos
apenas dizendo qual é o meu limite mínimo e máximo a ser considerado?
E qual é a minha meta de utilização como porcentagem?
E o DynamoDB tentará,
por exemplo, se tivermos uma capacidade máxima de 100,
ele a definirá como 100 WCU
se você estiver consumindo em média 70 WCUs e assim por diante.
Mas se você estiver consumindo, digamos, sete WCUs, o dimensionamento
automático entrará em ação automaticamente
e as unidades de capacidade desejadas serão 10 para essa tabela.
Portanto, o dimensionamento
automático é bom porque você não precisa
se preocupar muito em definir a WCU e a RCU.
Você só precisa pensar em qual é o meu mínimo,
qual é o meu máximo
e qual é a minha meta de utilização e o seu aplicativo, e o DynamoDB
fará o resto, o que é bom para ter um preço
melhor e um dimensionamento melhor.
Certo, isso se aplica tanto ao dimensionamento automático para leituras
quanto para gravações.
Portanto, isso é bom.
E então você obteria o custo estimado e assim por diante.
Portanto, se eu configurá-lo para Auto scaling max three and min one, e
novamente, max three and min one, e clicar
em save changes.
Agora, o que vou fazer
é esperar um pouco para que o dimensionamento
automático entre em ação e ver
as atividades de dimensionamento automático.
E, como podemos
ver, o Provisioned foi de dois e dois para WCUs e RCUs.
Mas tínhamos 1, 2, 3 em termos de intervalo para escalonamento automático e eu atualizo as
atividades de escalonamento automático.
E, como podemos ver nessa tabela, a configuração Capacidade
de leitura e foi definida como um e Capacidade de gravação foi
definida como um porque não
estou usando uma tabela.
Assim, o automóvel está sendo acionado e funcionou.
Portanto, se eu atualizar esta
página e remover isso
aqui, como podemos ver agora, a RCU e as WCUs são uma e uma.
Então, vou logo dizendo, é muito legal.
Funciona exatamente como
o EC2, mas para o DynamoDB.
Então é isso para esta palestra.
Espero que você tenha gostado.
E eu o verei na próxima palestra.
