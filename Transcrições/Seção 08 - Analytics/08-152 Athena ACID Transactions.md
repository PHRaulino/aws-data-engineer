Um novo recurso
Isso significa que temos garantias rigorosas
sobre as transações.
Assim, você pode ter usuários simultâneos acessando
a mesma linha ao mesmo tempo e fazer com que tudo funcione de forma consistente.
Sob o capô está o Apache Iceberg.
E para usá-lo, tudo o que você precisa
fazer é adicionar table_type igual a ICEBERG quando estiver
criando uma nova tabela no Athena usando o comando Create Table.
E isso permite que você, como
eu disse, tenha usuários simultâneos fazendo
modificações ou exclusões no nível da linha, seja o que for, sem se
preocupar com o fato de eles pisarem uns nos outros.
Na verdade, isso é compatível com o Elastic Map
Reduce, o Apache Spark e qualquer coisa que
suporte o formato de tabela do Apache Iceberg.
O bom é que isso elimina qualquer necessidade de bloqueio
de registro personalizado.
Portanto, sem o suporte a ACID, você precisaria ter algum tipo de solução
para bloquear um registro e desbloqueá-lo
em torno de qualquer modificação nele, de modo que, se duas pessoas
estivessem acessando o mesmo registro ao mesmo tempo
e tentando gravar nele, elas não estariam brigando
entre si.
Agora, o Iceberg e as transações ACID
fazem isso automaticamente para você.
Além disso, um pequeno benefício
colateral é que ele lhe dá o que chamamos de operações de viagem no tempo.
Portanto, você realmente pode recuperar dados que foram
excluídos recentemente, usando apenas
uma instrução select simples e antiga.
Portanto, alguns dos dados históricos que estão sendo mantidos
para fins de transações ACID podem ser usados
para essa finalidade.
Lembra-se de quando falamos sobre as tabelas governadas
na Formação do Lago?
Bem, essa é uma outra maneira de fazer a mesma coisa.
Portanto, as tabelas governadas nos deram suporte ACID em tabelas S3 no Lake Formation,
mas essa é outra maneira de obter recursos
acid com o Athena.
Assim, você poderia configurar uma tabela governada no Lake Formation
e, em seguida, acessar essa tabela com o Athena,
e você teria suporte ACID.
Essa é apenas outra maneira de fazer isso.
Portanto, você pode simplesmente criar uma tabela explicitamente
a partir do Athena diretamente com um tipo de tabela Iceberg, e você também terá
suporte ACID para isso.
Portanto, há duas maneiras diferentes
de resolver o mesmo problema.
Talvez você também se lembre de que, no Lake Formation,
com tabelas governadas, havia um recurso para
compactar automaticamente essas tabelas com o passar do tempo, pois, com
o passar do tempo, há uma espécie de sobrecarga
que se acumula e que pode, na verdade, diminuir o desempenho
com o passar do tempo.
Agora, com o Athena ACID, pelo menos por
enquanto, você precisa fazer isso periodicamente.
Portanto, se você estiver usando transações ácidas no Athena, provavelmente
desejará executar um comando como
esse de vez em quando.
Otimize a tabela, reescreva os dados usando BIN_PACK, em que
um catálogo é igual a qualquer coisa.
Portanto, um comando como esse
voltará e compactará seus dados que foram inchados
por esse suporte ACID ao longo do tempo e os tornará novamente eficientes.
Então, esse é o tipo de coisa que
eu poderia ver aparecendo nos exames,
esse tipo de trivialidade.
O que fazer se suas transações ACID estiverem
ficando mais lentas com o tempo?
Bem, a resposta seria
compactá-los periodicamente usando o comando
BIN_PACK que você está vendo aqui.
Esse é o Athena ACID em poucas palavras.
Um novo e empolgante recurso em 2022, à medida que
cada vez mais o mundo da análise de dados da AWS passa a
oferecer suporte a ACID.
