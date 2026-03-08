Vamos discutir os filtros de dados na formação de lagos,
Podemos fazer a segurança em nível
de coluna, linha ou célula usando filtros de dados.
Quando você está configurando a formação de lagos
no console, a aparência é esta.
Aqui, à direita, você verá uma pequena tela
de criação de filtro de dados.
Você pode dar um nome a esses dados, filtrar, informar a qual banco de
dados e tabela você está aplicando esse filtro e, em
seguida, a chave disso está lá
embaixo, onde diz acesso em nível de coluna e expressão de filtro de linha.
Assim, escolhendo coisas diferentes,
você pode obter segurança em nível de linha de coluna ou mesmo de célula.
Portanto, elas são aplicadas quando estamos concedendo
as permissões de seleção em uma tabela, e é aí que temos essa opção.
Então, digamos que eu queira ter segurança em nível de linha.
Eu faria isso selecionando o acesso
a todas as colunas no nível da coluna, mas
depois implementando uma expressão de filtro de linha
para ter uma segurança no nível da linha implementada
nesse filtro de dados.
Se eu quisesse segurança em nível de
coluna, deixaria o filtro de linha em branco e teria todas as linhas.
Mas então posso dizer incluir colunas
ou excluir colunas para fornecer segurança em nível de coluna
sob o acesso em nível de coluna.
E para a segurança em nível de célula, posso fazer as duas coisas.
Eu poderia dizer para incluir colunas específicas
ou excluir colunas específicas e
também aplicar uma expressão de filtro de linha.
Se eu estiver selecionando colunas
e linhas que são permitidas no meu
filtro, então agora tenho segurança no nível da célula.
Você pode fazer isso por meio do console, como
vemos aqui à direita, ou também pode
fazê-lo por meio da API, por meio da CLI.
Isso é criar células de dados.
Filter é o nome da chamada de API para isso.
