Sempre que você for testado
em SQL, provavelmente poderá esperar
ser testado sobre como funcionam os diferentes
tipos de junções. Esse é um dos tópicos favoritos do exame, não apenas
para este exame, mas para
qualquer exame em que o SQL esteja envolvido.
Então, vamos falar sobre os diferentes tipos de uniões.
Agora, por padrão, se você disser join no SQL,
o que obterá é um join interno.
Então, imagine que tenho duas tabelas chamadas
A e B, e ambas têm alguma coluna em comum, certo,
então talvez ambas sejam informações sobre
algum cliente, certo, e algumas informações
sobre esse cliente estão na tabela A, outras
informações estão na tabela B, mas elas estão
Portanto, se eu quiser fazer
referência a informações de ambas as tabelas, poderei fazer
uma união interna com base nessa união na tabela em que
desejo combiná-las.
Portanto, com uma união interna, só obterei resultados
para a interseção dessas duas tabelas,
para cada interseção em que houver um ID de cliente comum ou qualquer que seja o
identificador entre essas duas tabelas.
Vamos dar uma olhada em um exemplo para deixar isso um pouco mais claro.
Portanto, neste exemplo, estamos
vinculando duas tabelas chamadas clientes e pagamentos
no campo de número do cliente,
de modo que há um campo de número do cliente e um campo de
número do cliente de pagamento.
O que eu quero fazer nesse caso é selecionar o nome
do cliente na tabela de clientes
e a data e o valor do pagamento na tabela
de pagamentos, que estão vinculados
ao número do cliente.
Então, observe a sintaxe disso:
estamos dizendo select c. customerName, p. paymentDate,
p. amount from customer C, portanto,
estamos atribuindo um alias de C à tabela de clientes para que eu possa
me referir a ela na instrução select
como apenas C em vez de clientes, que eu vou
dizer inner join payments P, novamente, estamos
atribuindo um alias de P à tabela de pagamentos para que eu
possa me referir aos pagamentos como apenas P.
Em c. customerNumber, o que significa que o campo do
número do cliente na tabela do cliente é igual a p. customerNumber e, devido a esse alias,
isso significa o número
do cliente na tabela de pagamentos.
Portanto, a junção interna só me dará resultados em
registros que tenham uma correspondência,
em que haja um número de cliente em comum entre
a tabela de clientes e a tabela de pagamentos.
E quando houver um número de cliente em comum, selecionarei o nome
do cliente, a data de pagamento
e o valor.
E este é um exemplo desses resultados aqui.
Portanto, novamente, a junção interna, o tipo de junção
padrão, se você disser apenas
junção, só fornecerá resultados para a interseção
em que a condição na qual você está fazendo a junção existe
em ambas as tabelas.
(Também poderíamos
fazer o que chamamos de união externa
esquerda e, nesse caso, obteremos
resultados para tudo na tabela A, independentemente
de ter ou não um identificador correspondente na tabela B.
Portanto, neste exemplo aqui, a mesma coisa, exceto que
estamos dizendo união à esquerda.
Essa é a única diferença nessa consulta.
Mas você pode ver agora que temos alguns resultados
nulos, certo? Portanto, para a American Souvenirs Incorporated
e a Porto Imports Corporation, seja lá o que for, temos resultados
nulos para a data e o valor do pagamento porque, presumivelmente,
não havia nenhum número de cliente correspondente na tabela de pagamentos para esse número de cliente
na tabela de clientes.
Portanto, para qualquer que seja a tabela da esquerda,
obteremos tudo dessa tabela, independentemente
de ter ou não uma correspondência
e, se não tiver uma correspondência na tabela da direita,
obteremos um resultado nulo no que estamos tentando
selecionar na tabela da direita.
Também podemos fazer uma junção externa
direita, exatamente a mesma ideia, exceto pelo
fato de que o que faremos é obter tudo da tabela direita,
independentemente de corresponder ou não,
mas não tudo da tabela esquerda.
Portanto, a mesma sintaxe aqui, estamos dizendo right join desta vez, e tudo o que isso significa
é que, qualquer que seja a tabela
que tenhamos no lado direito, obteremos tudo, independentemente
de ter ou não uma correspondência,
no lado esquerdo, mas não necessariamente tudo do lado
esquerdo que não tenha uma correspondência para
o direito.
Você também pode fazer uma junção externa completa,
que fornecerá os resultados de tudo
na tabela A e na tabela B, independentemente de haver ou não
uma correspondência; se houver uma
correspondência, você obterá resultados para essa instrução
de junção; caso contrário, obterá resultados
nulos, certo?
Isso geralmente é usado para depuração e solução de problemas,
portanto, se você quiser ter uma boa
ideia de onde há dados incompatíveis, onde
não há chaves correspondentes nessas duas
tabelas, essa pode ser uma boa
maneira de pesquisar e ver
onde há IDs que não correspondem em ambas
as tabelas por algum motivo.
Por fim, podemos ter uma junção externa cruzada. Não
consigo pensar em muitos motivos para fazer isso.
O que uma junção externa
cruzada faz é fornecer um resultado para cada combinação possível entre
as duas tabelas A e B, portanto,
para cada linha da coluna A, fornecerei um resultado
para cada combinação
de A e B juntos.
E, como você pode imaginar,
isso é muito, muito, muito rápido, portanto,
não há muitos motivos para fazer isso, mas, só para completar,
é isso que uma junção externa cruzada faz:
ela fornece todas as combinações
possíveis entre A e B, independentemente
de elas corresponderem ou não.
E, apenas para completar, esta
é a aparência dessa sintaxe, a junção cruzada é
uma sintaxe para isso e, mais uma vez, ela
fornecerá muitos, muitos,
muitos, muitos, muitos, muitos resultados, pois
está fornecendo todas as combinações possíveis entre
os clientes e os pavimentos.
