de informações pessoais ou confidenciais é algo chamado
de salga de chaves.
Portanto, se você for fazer o hash de algum número de
cartão de crédito ou senha ou algo do gênero,
a ideia de salting é uma pendência ou um pré-end.
Algum valor aleatório conhecido como assalto à parte dos
dados, que pode ser a senha antes de fazer o hash.
Isso evita que as pessoas façam o que chamamos
de ataques de tabela arco-íris,
em que elas simplesmente têm uma lista de senhas já usadas ou uma lista de senhas
que obtiveram de alguma
fonte nefasta e percorrem toda a tabela tentando
encontrar correspondências.
Portanto, se as senhas que você está armazenando tiverem
algum tipo de informação aleatória presa no início
ou no final, isso impedirá as tentativas de adivinhar quais
são essas senhas.
Isso garante que a mesma parte dos dados,
como duas senhas idênticas, não produza o mesmo hash em instâncias
diferentes devido ao valor de sal
exclusivo que foi adicionado na frente
dela.
Ou, no final das contas, uma prática recomendada é garantir
que seus sais sejam fortes,
criptograficamente seguros, de valor aleatório, para que ninguém possa tentar
adivinhar o que eles são.
E você também deve alternar esses sais periodicamente
para dificultar ainda mais o processo.
Portanto, se alguém descobrir sua lista de valores de sal, você
não estará necessariamente em apuros.
Você também deve certificar-se de que cada usuário
tenha seu próprio valor de
sal exclusivo, para não reutilizar o mesmo sal em todos os usuários.
Então, se alguém descobrir qual
é o valor desse sal, você está acabado, certo?
Não há mais razão para isso.
Portanto, uma prática melhor é ter
valores de sal exclusivos para cada usuário.
Portanto, o que você deve fazer é salgar e, em seguida, fazer o hash de suas senhas
ou do que quer que seja antes de armazená-las.
Dessa forma, o valor armazenado
para essa senha será muito mais difícil de ser decifrado
devido ao valor aleatório do sal que faz parte dela.
Para tornar isso real com um exemplo, digamos
que temos o usuário um e o usuário dois, e
ambos têm a mesma senha.
Eles não são muito bons em criar senhas,
portanto, a senha deles é senha, 1, 2, 3.
No entanto, ambos têm valores de sal exclusivos que são aleatórios
e criptograficamente seguros, associados
a cada usuário.
Portanto, o usuário um tem um valor de sal.
O usuário dois tem um valor de sal diferente
e, se colocarmos cada valor de
sal após essa cadeia de senhas, você poderá ver que, depois
de fazer o hash com o algoritmo SHA 2 56, elas parecerão completamente
diferentes uma da outra, embora ambas codifiquem
exatamente a mesma senha.
Portanto, esse é um pequeno truque para ser mais seguro na forma como você
armazena suas informações pessoais identificáveis.
E, desde que você saiba qual é o salt para cada usuário,
ainda poderá criar o mesmo valor de hash para a senha desse usuário
e garantir que eles se comparem e correspondam
adequadamente em seus aplicativos.
