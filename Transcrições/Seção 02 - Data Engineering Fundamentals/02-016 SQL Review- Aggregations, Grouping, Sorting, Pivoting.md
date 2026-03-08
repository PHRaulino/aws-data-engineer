O guia do exame diz que você precisa conhecer
a linguagem de consulta estruturada ou SQL e algumas coisas
específicas que deseja fazer com o SQL.
Então, vamos fazer nossa análise aqui.
Agora vou presumir que você sabe o que é SQL.
Se você é um completo iniciante em
SQL, nunca fez isso
antes e não tem a menor ideia do que essa
coisa na tela significa, eu sugeriria adicionar
um curso de SQL ao seu caminho de aprendizado
para esse exame.
Não posso incluir um curso completo sobre SQL
como parte deste curso.
Esta será apenas uma rápida revisão
de alguns dos principais pontos
que o exame espera que você compreenda.
Se você precisar se aprofundar
mais nesse assunto, há muitos cursos excelentes de SQL no mercado.
Basta encontrar o mais popular e você
Eles dizem que você precisa entender de agregação,
o que é bastante básico, então vamos começar por aí.
Se você já usou algum SQL, sabe
como obter o número de linhas em uma tabela.
Você simplesmente diz SELECT COUNT(*).
E, neste exemplo, estou dizendo AS total_rows.
AS está apenas atribuindo o nome da coluna que
eu verei nos resultados dessa consulta.
E FROM employees significa que estou contando-os
a partir da tabela chamada employees, de modo
que isso me dará o número total de linhas da tabela de
funcionários.
COUNT(*) faz isso.
Se eu quiser somar todos
os salários na tabela de funcionários, posso
dizer SUM(salary).
E exibir esse resultado
em uma coluna chamada total_salary neste exemplo.
Se eu quiser obter o salário médio,
a AVG é a operadora para isso.
Eu poderia simplesmente dizer AVG(salary) AS average_salary.
Novamente, o AS está apenas nomeando a coluna que
contém o resultado da tabela do funcionário.
E também posso obter o máximo e o mínimo.
Portanto, se eu quisesse obter o salário máximo,
o salário mais bem pago em toda a nossa tabela, poderia
dizer SELECT MAX(salary) e chamar esse resultado
de highest_salary FROM employees, ou seja, coisas bem
básicas.
Se isso não fizer sentido para você, novamente,
talvez seja melhor fazer um curso de SQL separado,
pois esta é apenas uma revisão rápida.
Uma coisa um pouco mais básica é usar a instrução
CASE, vamos falar sobre esse truque, então
o contexto aqui é tentar aplicar filtros aos resultados
quando estiver agregando.
Agora, se você precisar filtrar apenas uma condição,
não precisará de uma instrução
CASE, basta usar uma cláusula WHERE,
o que é muito comum, certo?
Portanto, se eu quisesse obter o número total de funcionários,
mas quisesse apenas o número
de funcionários que ganham
mais de US$ 70.000, libras, qualquer que seja sua unidade
monetária, eu poderia simplesmente
acrescentar WHERE salary > 70.000 no final dessa declaração, certo?
Então, o que isso vai fazer é dizer SELECT
COUNT(*) AS high_salary_count.
Portanto, vou ter uma coluna chamada contagem de salário
alto na tabela de funcionários.
Mas, em vez de contar todas as linhas dessa
tabela, vou contar
apenas as linhas em que a coluna de salário for maior que 70.000.
Faz sentido?
E se eu quiser usar mais de uma cláusula
WHERE, certo?
E se eu tiver mais de um filtro que eu queira fazer?
Bem, uma maneira de fazer isso é com uma instrução CASE.
Portanto, a cláusula CASE permite que você especifique alguma condição
e, na verdade, posso fazer mais de uma por vez aqui.
O problema com a cláusula
WHERE é que, como você a especifica
após a instrução de agregação, só posso filtrar
uma coisa de cada vez usando uma cláusula
WHERE.
Mas se eu mover esse filtro dentro do próprio SELECT, poderei fazer mais de
uma coisa ao mesmo tempo.
Portanto, neste exemplo aqui, estou dizendo SELECT
COUNT (CASE WHEN salary > 70.000 THEN
1 END), o que isso faz?
Isso significa
que vou aplicar essa pequena lógica
aqui em que, para cada linha, se o salário for maior que
70.000, vou retornar o valor um.
Tudo bem?
Isso me dará uma contagem
de todos os valores que têm um porque têm
mais de 70.000 e essa conta será exibida
como conta de salário alto.
Ao mesmo tempo, tenho outra cláusula aqui (CASE
WHEN salary BETWEEN 50,000 and 70,000 THEN 1), portanto, a cláusula then significa
apenas que vou somar essa cláusula para obter o número
total de contagens para essa condição, e eu chamaria essa
contagem de salário médio.
E, da mesma forma, para qualquer pessoa com menos de
50.000, a mesma ideia, apenas (CASE WHEN salary < 50.000 THEN 1 END)
e isso contará todos os que resultarem dessa
condição e exibirá isso como contagem
de salários baixos.
Portanto, um pequeno truque para fazer vários filtros de uma só vez usando
a instrução CASE, talvez você
nunca tenha visto isso antes.
Revisão rápida do agrupamento aqui.
E se eu quiser dividir as coisas
e separá-las por um determinado campo?
Então, neste exemplo, quero contar quantos
funcionários há em cada departamento?
Vamos imaginar que nossa tabela de funcionários
tenha uma coluna department_id para cada pessoa e poderíamos
fazer algo assim.
Portanto, SELECT department_id, COUNT(*) AS number_of_employees.
Isso exibirá o resultado da coluna department_id e, em seguida, o número
total dos resultados que vou consultar
e rotulará esse resultado
como número de funcionários.
Da mesa do funcionário.
Estamos aplicando uma condição aqui
apenas por diversão, onde join_date > 1º de janeiro de 2020.
Ah, cara, se eles soubessem no que estavam se
metendo dali a alguns meses.
E vamos dizer GROUP BY department_id.
Esse é o ponto aqui, portanto, isso é agrupamento.
Ao dizer GROUP BY department_id, obterei uma linha
diferente em meus resultados para cada
department_id exclusivo que existe
na tabela do funcionário.
Aqui está um exemplo de saída disso.
Ele teria o department_id
e o número de funcionários,
esses são os rótulos
que selecionei na instrução SELECT.
Onde estão todas as pessoas
que ingressaram depois de 1º de janeiro de 2020, mas agrupadas
por seu department_id.
Portanto, estou vendo
aqui que há um total de cinco funcionários no departamento de
RH que ingressaram após 1º de janeiro de 2020.
E um total de oito funcionários do departamento de TI que
ingressaram após 1º de janeiro de 2020.
Portanto, apenas um lembrete de como funciona o GROUP BY.
Também podemos GOURP BY mais de uma coisa e chamamos
isso de agrupamento aninhado.
Então, se eu disser GROUP BY sale_year, product_id, o que está acontecendo
aqui?
Este é um exemplo diferente.
Digamos que temos uma tabela de vendas aqui onde temos, quando as
coisas foram vendidas, qual produto foi vendido
e por quanto, certo?
Portanto, aqui estamos dizendo para selecionar o ano da data
de venda e exibi-lo como sale_year.
E a próxima coisa que teremos,
a próxima coluna em nossos resultados é apenas o product_id.
E a soma de todos os valores para esse
product_id naquele ano é o que isso significa.
E vamos chamar essa soma final de vendas totais.
FROM sales, esse é apenas
o nome da tabela com a qual estamos trabalhando.
Em seguida, vamos dizer GROUP BY sale_year, product_id.
Agora, o sale_year do topo acima está
se referindo apenas ao ano da data de venda, certo?
Portanto, vamos agrupar pelo ano em que a venda foi
feita e também pelo product_id individual.
Portanto, o que isso fará
é me fornecer linhas individuais no
resultado para cada combinação do ano de venda e do product_id.
Portanto, para cada produto,
verei os resultados de cada ano.
Agora, e se eu quiser fazer o pedido de acordo com um critério específico?
É isso que o ORDER BY está fazendo, está classificando meus resultados.
Nesse caso, estamos ordenando por sale_year
e, em seguida, por total_sales em ordem decrescente.
Portanto, o que isso está me fornecendo
é uma tabela que, para cada ano, me dará a lista de product_ids que foram
vendidos naquele ano, classificados pelo
número total de vendas, o valor total da venda do produto naquele
ano.
Portanto, um exemplo um pouco mais complicado de agrupamento
aninhado e classificação ao mesmo tempo.
Portanto, tente entender isso.
Também vale a pena falar sobre o pivotamento.
Normalmente, quando falamos
de pivôs, é no contexto de uma planilha do Microsoft Excel
ou algo parecido,
mas também é possível pivotar em uma planilha,
é possível.
A sintaxe varia de acordo com o banco de dados em que você está.
Portanto, eu não esperaria que o exame o questionasse sobre
a sintaxe específica de como funciona o pivotamento.
Portanto, não se preocupe muito com a sintaxe e
como tudo funciona no nível do SQL, pois
duvido que eles o questionem sobre isso.
O ponto importante é apenas saber o que é pivotar.
Portanto, a principal conclusão aqui é que
a dinamização é o ato de transformar dados em nível de linha em
dados em colunas, certo?
Então, pego uma mesa e a viro no set.
E como isso funciona, mais uma vez, é específico do banco de dados.
Alguns têm um comando PIVOT.
Portanto, aqui está um exemplo
de um banco de dados que tem um comando PIVOT.
Queremos começar de dentro dessa consulta, certo?
Então, vamos dar uma olhada na segunda instrução SELECT
nessa consulta, onde está
escrito SELECT salesperson, month, sales FROM sales AS sourceTable,
certo?
Então, vamos imaginar que temos uma tabela
de vendas que contém valores de vendas e o vendedor em
cada linha, mas queremos fazer um relatório por vendedor.
Portanto, para fazer isso, precisamos inverter as coisas, certo?
Portanto, é isso que essa declaração PIVOT no meio está fazendo.
Estamos dizendo que o pivô é o número total de vendas para cada mês
em janeiro e fevereiro.
Portanto, vamos somar as vendas de janeiro e as
vendas de fevereiro e inverter isso,
e chamaremos essa tabela dinâmica.
A partir dessa tabela dinâmica,
selecionaremos o vendedor, o mês e o número
total de vendas dessa tabela dinâmica.
E vamos chamar isso de sourceTable.
Fora isso, temos outra instrução SELECT que, na verdade,
está apenas renomeando esses resultados.
Portanto, estamos dizendo
que, para janeiro, chamaremos Jan_sales
e, para fevereiro, chamaremos Feb_sales.
E a saída aqui é o resultado dinamizado em que, em
vez de uma linha que tem o vendedor em quantidade, agora temos
uma linha para cada vendedor individual e a soma de suas vendas
em cada mês de janeiro
e fevereiro.
Portanto, o PIVOT é uma maneira de fazer isso.
Outra maneira mais portátil é
usar apenas a agregação condicional.
Então, novamente,
podemos voltar à nossa amiga cláusula CASE.
Poderíamos ter feito a mesma
coisa dizendo apenas SELECT salesperson SUM (CASE WHEN month
= January THEN sales ELSE 0).
Nesse caso, vamos somar os resultados
de todas as vendas que ocorreram no mês de janeiro.
E se não foi um mês de janeiro,
então somaremos zero para não contarmos
nenhum outro mês nesse caso.
A mesma coisa para fevereiro
e obtemos exatamente os mesmos resultados dessa forma.
Portanto, talvez seja uma maneira
um pouco estranha de usar a agregação para fazer um pivô.
Talvez não seja a maneira mais eficiente de fazer isso,
mas se você não tiver uma operação de pivô específica, essa é outra
maneira de fazer isso.
Novamente, a principal conclusão aqui
é que a dinamização é uma forma de pegar as informações no nível da linha e torná-las
colunares.
É só virar uma mesa.
