do Databrew.
Então, vamos nos distrair um pouco nesse mundo.
Falamos sobre algumas dessas técnicas anteriormente no curso, mas apenas para reforçar
a relação entre elas e o Databrew, uma maneira de lidar com PII é por meio da substituição.
Portanto, eu poderia simplesmente substituir isso por algum tipo de número aleatório.
Certo.
E substitua essas informações por algo que não seja pessoalmente identificável.
Eu poderia embaralhá-lo.
Eu poderia pegar todos os valores de PII em minhas linhas e embaralhá-los, de modo que o número do cartão de crédito da pessoa A pudesse ser
associado à pessoa B em vez de aos números de cartão de crédito, embora provavelmente não seja uma boa ideia
ter números brutos de cartão de crédito flutuando por aí.
A criptografia determinística é uma maneira de criptografar essas informações de identificação
pessoal de forma que um determinado valor sempre resulte no mesmo valor criptografado.
É determinístico.
Dessa forma, você também pode ter uma criptografia probabilística, que é um sistema em que pode haver mais
de um resultado de uma criptografia de um determinado campo.
Você também pode descriptografar algo que foi criptografado usando um comando decrypt, e provavelmente não
há melhor maneira de lidar com PII do que não tê-las em primeiro lugar.
Se você quiser anulá-lo ou simplesmente excluí-lo.
A transformação de exclusão pode ser usada para eliminar totalmente essas informações.
Você também pode ocultar informações de identificação pessoal.
Portanto, muitas vezes você verá apenas os quatro últimos dígitos de um cartão de crédito ou de um número de previdência
social sendo exibidos, sendo que o restante está mascarado ou embaralhado de alguma forma.
O mascaramento é uma forma de fazer isso.
E, por fim, há o hashing, em que você aplica algum tipo de função de hash ao valor de forma criptográfica.
No entanto, o hash é um pouco diferente, pois vários valores podem ter o mesmo resultado.
Então, às vezes, não há problema, mas isso também proporciona algum anonimato ao que você está fazendo.
Portanto, algumas técnicas para lidar com informações de identificação pessoal em bancos de dados.
Transformações.
E esses são os nomes específicos das transformações associadas a cada técnica.
