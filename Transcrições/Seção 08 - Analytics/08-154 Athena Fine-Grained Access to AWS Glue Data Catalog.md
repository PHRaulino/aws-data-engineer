access to AWS Glue Data catalog.
Não é uma granulação fina no sentido tradicional.
A ideia é que tenhamos um banco de dados baseado em IAM e segurança
em nível de tabela para operações específicas.
Portanto, isso é mais amplo do que os filtros de dados na formação de lagos.
Não estamos aplicando a segurança no nível da célula, da
linha ou da coluna aqui.
Trata-se mais das operações que podemos realizar nos
bancos de dados e tabelas do catálogo do Glue Data.
Você também não pode restringir isso a versões específicas da tabela.
Isso se aplica a tudo.
Agora, no mínimo, você precisa ter uma política de IAM
para o Athena que conceda acesso ao banco de
dados e ao catálogo de dados do glue em cada região.
Mas podemos fazer mais. Também podemos bloquear
as coisas se quisermos.
Portanto, você pode ter políticas configuradas
no IAM que podem restringir o acesso a operações de alteração
ou criação de bancos de dados para a criação de novas tabelas, para descartar
bancos de dados ou descartar tabelas,
para reparar tabelas ou até mesmo para mostrar todos os bancos
de dados ou todas as tabelas.
Portanto, essas são coisas que você pode bloquear usando
o IAM e o Athena Acesso refinado ao catálogo do AWS Glue.
Tudo o que você precisa fazer é
descobrir o mapeamento dessas operações para suas ações de IAM subjacentes,
o que nem sempre é simples.
Portanto, aqui está um exemplo
à direita para controlar o acesso à tabela suspensa.
Aqui estamos dizendo que permitiremos as ações necessárias
para descartar uma tabela em um catálogo específico,
em um banco de dados específico
e também em uma tabela específica dentro desse banco de dados.
E acontece que, para eliminar uma tabela, você precisa de acesso
para obter a partição e as partições em que essa tabela está.
Você precisa obter a tabela e o banco de dados
em que ela se encontra e precisa de permissão para excluir
a tabela e também a partição em que ela se encontra.
Portanto, você precisa procurar quais são essas ações
para uma determinada operação que esteja documentada.
No entanto, há um pequeno link lá, caso
você precise consultá-lo.
Não consigo imaginar que eles esperariam que você memorizasse
esse material para o exame.
No entanto, você pode usar seu bom senso para descobrir quais ações
podem corresponder a diferentes
operações de banco de dados que você pode
querer bloquear usando o Athena Fine-grained access to AWS
Glue Data catalog.
