Então, vamos
dar uma olhada nessas chamadas de API de dados que podemos fazer.
Então, se eu for para a minha tabela, como podemos ver agora,
estamos em "Scan" e podemos selecionar uma tabela, e depois clicamos
em "Run".
Portanto, "Scan" fará a varredura de toda
a tabela e, obviamente, retornará muitos itens para nós.
Se quiséssemos criar um item, poderíamos
Alice, quatro, cinco, seis.
Em seguida, especificamos um registro de
data e hora, portanto, deixe-me fazer isso rapidamente.
E então, T zero
cinco, zero seis e seu zero.
Aqui vamos nós.
Ok, e depois alguns conteúdos para ele.
Blog da Alice, ok.
Agora, vamos criar esse item.
Portanto, esse foi um item colocado.
Isso porque enviamos um novo item para o DynamoDB e especificamos o registro de data
e hora da postagem do ID do usuário, e esse
item era novo, portanto, foi criado.
Se você quiser ver o item de atualização, o que
posso fazer é "Actions" (Ações) e depois "Edits" (Edições).
Em seguida, editaremos apenas um atributo
específico, por isso editei o blog da Alice, cliquei
em salvar alteração e, nos bastidores,
faremos uma chamada à API do item de atualizações.
Portanto, vimos atualizações.
Agora vamos dar uma olhada
nos gets, então, se eu clicar neste, por exemplo, entrarei
no "Editor de itens".
Bem, nos bastidores, ao clicar nessa
linha, nesse item, consegui recuperar o conteúdo desse
item e, portanto, esse foi um get_item que foi feito.
Então, isso é bom.
Agora, obviamente, podemos realizar ações em lote, portanto, podemos
clicar em "Actions" (Ações) e depois em "Delete Items" (Excluir itens),
que deve ser um item de exclusão em lote.
Certo, então gravações em lote e exclusões em lote.
Mas, se você quisesse excluir tudo da tabela, poderia
fazer uma "varredura" e uma exclusão em lote, mas isso
não seria muito eficiente.
A outra maneira de fazer isso seria simplesmente eliminar
a tabela e pronto.
Agora, finalmente, vamos dar uma olhada em "Scan" e "Query".
Portanto, a varredura realmente fornece todas as tabelas que você tem e, em seguida,
você pode aplicar um filtro, se quiser,
mas isso é feito no lado do cliente para esse filtro,
portanto, ele será filtrado no navegador da Web, não
diretamente no DynamoDB.
Ou você pode fazer uma consulta.
E uma consulta é muito útil porque podemos especificar um ID de
usuário específico.
Por exemplo, John, um, dois, três e, em seguida, clique
em "Run" (Executar).
E isso nos dá todos os itens de João um, dois e três.
Mas também poderíamos ter uma consulta e especificar uma condição no registro de data
e hora da postagem, que é uma chave de classificação.
Portanto, podemos ter igual a, menor que igual a,
maior que, entre e começa com.
Portanto, se você quiser saber todas as postagens depois de, digamos,
2021-11, e clicar em "Run" (Executar), obteremos apenas
um item de retorno.
Mas, então, se fizermos 21, 2021-09, receberemos dois itens de volta.
Portanto, como podemos ver, a consulta aqui é feita apenas no ID do usuário e no registro de data
e hora da postagem.
Não precisamos fazer isso,
não podemos consultar o conteúdo ou pesquisar no conteúdo.
Se quisermos, podemos filtrar o conteúdo posteriormente, mas
isso será feito no lado do cliente.
Portanto, isso realmente mostra o poder do uso de chaves de partição,
como uma chave de hash e uma chave de classificação, certo?
Então é isso, já vimos todas as APIs do DynamoDB.
Agora, vamos fazer uma varredura e recuperar todos os dados.
Portanto, espero que tenham gostado
desta palestra e nos veremos na próxima.
