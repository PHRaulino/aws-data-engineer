Quero falar um
pouco sobre expressões regulares em SQL,
e as expressões regulares poderiam ser
o tema de um curso inteiro,
portanto, vou lhe dar apenas o básico aqui.
Mas, em um nível mais alto,
uma expressão regular é apenas uma linguagem de correspondência de padrões.
Portanto, é uma maneira de pesquisar padrões em uma cadeia de caracteres dentro de uma coluna
no seu banco de dados, como talvez
uma substring dentro de uma cadeia de caracteres maior, ou
ser usado para analisar informações de uma cadeia de
caracteres maior, como, por exemplo, texto
em um arquivo de registro ou algo assim.
Pense nisso como uma versão muito mais
avançada do operador LIKE,
em que você está fazendo uma espécie de pesquisa difusa,
não uma correspondência exata em uma
coluna, mas quer fazer algo que seja um
pouco mais avançado e complexo.
O Tilde costuma ser o operador de expressão regular.
Portanto, se você disser where til,
isso significa que você fará uma correspondência
com uma expressão regular e não com uma string literal.
E o til star significa que você está fazendo a mesma coisa,
mas não diferencia maiúsculas de minúsculas.
Portanto, se você quiser fazer uma pesquisa que diferencie maiúsculas de minúsculas,
use o til; se não diferenciar maiúsculas de minúsculas, use o til estrela.
E o operador de bang, o ponto de exclamação, por que isso
é tão difícil de dizer?
É claro que não significa como normalmente acontece.
Assim, por exemplo, o ponto de exclamação til estrela significaria, em uma maneira
que não diferencia maiúsculas
de minúsculas, não corresponder à seguinte expressão.
Vamos dar uma olhada em alguns exemplos aqui.
Portanto, a sintaxe de expressão regular básica real aqui.
Provavelmente, não se espera
que você saiba mais do que isso para o exame,
mas há muito mais profundidade
aqui se você quiser mergulhar na toca do coelho das expressões regulares.
O acento circunflexo, esse símbolo, significa que você está correspondendo
a um padrão no início de uma cadeia de caracteres, e o cifrão significa
que você deseja corresponder a um padrão no final de uma cadeia
de caracteres.
Assim, por exemplo, se sua expressão regular fosse o cifrão
boo, isso corresponderia à palavra boo, porque o final da palavra
boo corresponde a boo, mas não corresponderia à palavra
book porque há um K no final e eu disse
que quero corresponder
a isso no final.
No entanto, o caret boo corresponderia a ambos, certo?
Porque boo está no início de
ambos os termos, boo e book.
Portanto, a expressão regular caret boo
corresponderia a boo e book.
O cifrão boo, entretanto, só corresponderia a boo porque isso
significa que estou correspondendo ao final da cadeia de caracteres.
Além disso, se você quiser combinar
mais de uma coisa, se quiser fazer uma espécie de operação
OR, é isso que o operador pipe faz.
Isso lhe dá um conjunto alternativo de caracteres que você
está procurando.
Assim, por exemplo, sit pipe set corresponderia a sit ou sat
na string que você está pesquisando
na coluna em que está pesquisando.
Você também pode usar intervalos de caracteres.
Portanto, entre colchetes, se eu disser A a Z minúsculo,
isso corresponderá a qualquer letra minúscula entre A e Z.
E você pode combiná-los com muitos intervalos, certo?
Portanto, eu poderia dizer A a Z e letras maiúsculas de A a Z e de
zero a nove, por exemplo, se
quisesse combinar todos os números e letras
maiúsculas ou minúsculas.
Isso, por si só, não é muito útil.
Se eu quisesse corresponder, digamos, a uma palavra com quatro letras minúsculas,
você poderia usar o operador de colchetes para dizer quantas
dessas correspondências deseja.
Portanto, colchetes de A a Z e, em seguida, colchetes
curvos de quatro significa que
quero corresponder a qualquer palavra de quatro letras minúsculas
em que a palavra seja composta de letras
minúsculas entre A e Z.
Entendeu até agora?
E, por fim, há alguns metacaracteres especiais que
você talvez queira conhecer.
A barra invertida D corresponderá a qualquer dígito,
a barra invertida W corresponderá a qualquer letra, dígito ou sublinhado, a barra invertida
S corresponderá a qualquer espaço em branco, como um espaço
ou uma tabulação, e a barra invertida T corresponderá
especificamente a uma tabulação.
Portanto, esses são apenas alguns atalhos úteis
para suas expressões regulares.
Em vez de dizer colchete zero traço nove, eu poderia
dizer apenas barra invertida D para
corresponder a qualquer dígito, por exemplo.
E aqui está um exemplo concreto de como
isso realmente funciona em uma consulta SQL real.
Digamos que eu queira pesquisar todas
as linhas em que o nome comece com fogo ou gelo.
Não sei, talvez esses sejam nomes
de elementos míticos ou algo assim, certo?
A sintaxe para isso pode ser select
star from whatever the name of the
table is, where name til star e, entre aspas simples,
a própria expressão, caret e, entre
parênteses, fire pipe ice.
Vamos detalhar isso.
Portanto, concentre-se na cláusula where,
where, name til star.
Isso significa que é uma correspondência de expressão regular que não diferencia maiúsculas
de minúsculas; as aspas contêm a própria expressão regular.
O acento circunflexo novamente significa que ele precisa corresponder
ao início da cadeia de caracteres.
Portanto, a cadeia de caracteres encontrada na coluna
de nome em cada linha precisa começar com fogo ou gelo, certo?
É isso que o tubo significa, ou ou, certo?
Então é isso.
É simples assim.
Portanto, lembre-se de algumas dessas
noções básicas de expressões regulares, como é
a sintaxe e, com sorte, você não ficará confuso
quando vir tildes e outros e caretas e outros em um comando SQL.
