usuários e nela vamos habilitar o
fluxo do DynamoDB.
Para isso, vamos para exportações e
fluxos,
e aqui teremos os detalhes do
fluxo do DynamoDB, e vamos habilitá-lo.
Agora temos a opção de escolher
o tipo de visualização que queremos
ter em nosso fluxo do DynamoDB.
E pode ser atributos-chave, nova imagem,
todas
as imagens ou imagens novas e antigas.
Portanto, manterei a última opção para
obter o máximo de informações
possível e habilitarei esse fluxo.
Ok, ótimo.
Portanto, agora meu fluxo está ativado e,
dentro
dele, como você pode ver, se eu rolar
a tela para baixo, há o acionador.
E o acionador é o
que esse fluxo vai acionar?
Assim, podemos criar um acionador.
E aqui temos uma função Lambda que pode
ser
chamada sempre que o fluxo do DynamoDB for
atualizado.
Então, para isso, vamos
criar uma nova função.
Está bem.
E podemos usar um modelo.
E aqui posso digitar DynamoDB, e temos
o fluxo de processo DynamoDB Python.
Que registrará todas as atualizações
feitas em uma tabela.
Portanto, isso é bom.
Vamos configurá-lo e eu o chamarei
de Lambda demo, fluxo do DynamoDB.
Em seguida, criaremos uma nova função com
permissões básicas do Lambda e nos
certificaremos
de editar essa função para adicionar
as permissões de leitura do DynamoDB.
Agora, para os acionadores do
DynamoDB, precisamos criar o acionador.
Então, será a postagem do
usuário. Qual era a tabela?
A tabela de postagens dos
usuários? Sim, de fato.
E o tamanho do lote é 100.
Está bem.
Portanto, esse é o número de registros que
serão lidos por vez.
A janela de lote, se você
quiser reunir registros antes de chamar
as funções, para ser mais eficiente.
E a posição inicial.
Portanto, você deseja ler do início
ou do final do fluxo, caso
o fluxo já tenha sido criado.
Portanto, estamos bem.
Ativamos o acionador.
E, como você pode ver, o
que ele faz é apenas imprimir
os registros que obtemos do fluxo
para os logs que poderemos
ver nos logs do CloudWatch.
Portanto, agora criamos a função, mas
recebemos
um erro, ou seja, o registro ou
a função não pode acessar nosso
fluxo porque faltam informações do IAM.
Portanto, vamos corrigir isso.
Então, clicamos em nossa função
e, em seguida, em configuração,
vamos para permissões, e esta
é a função de execução.
Agora temos que clicar nessa função
de execução e adicionar as permissões
necessárias para ler do DynamoDB.
Portanto, anexaremos uma política e
procuraremos
o DynamoDB, e teremos o
acesso somente leitura do DynamoDB,
porque o que estamos fazendo
é realmente ler do DynamoDB.
Portanto, isso é bom.
E este também é bom
para ler no DynamoDB.
Portanto, vamos anexar esses dois por
precaução,
mas isso se aplica ao Lambda.
Portanto, provavelmente um pouco melhor.
Portanto, vamos anexar essa política e,
para
ser honesto, uma delas vai funcionar.
Estou tentando simplificar o máximo
possível, e é por
isso que não estou gastando muito tempo
com isso.
Então, vamos atualizar esta página e
parece que estamos prontos para começar.
Portanto, temos mais ações no DynamoDB.
Portanto, isso é bom.
Está bem.
E agora, se atualizarmos isso, podemos
escolher essa função e definir
o tamanho do lote em
100 e criar esse acionador.
Isso significa que meu fluxo do
DynamoDB acionará minha função Lambda.
E se eu voltar à minha
função Lambda e atualizar essa página,
poderemos ver que o DynamoDB está
de fato acionando minha função Lambda.
Portanto, esse é um tipo de
integração habilitado com essas
configurações.
Muito bem.
Então, a seguir, o que vou fazer é
testá-lo.
Então, vamos para a nossa tabela e o
que vou fazer é clicar em exibir itens.
E vamos fazer algumas coisas.
Por exemplo, vamos pegar este item, a
segunda postagem do John, vamos para a
ação, editá-la e, em seguida, vou
modificar.
Portanto, vou dizer uma segunda edição do
post "yay".
E clique em salvar a alteração.
Portanto, isso é bom.
Em seguida, pegaremos a
Alice, faremos uma ação
e depois duplicaremos.
Portanto, ele criará uma nova coisa e
eu adicionarei um pouco mais de dados
como um novo blog da Alice
e, em seguida, criarei um item.
E, finalmente, não gostamos deste
blog, portanto, vou excluí-lo.
Portanto, vou realizar a ação e depois
excluir os itens.
E sim.
Está bem.
Portanto, realizamos três tipos de
operações.
Tivemos uma atualização, uma criação e uma
exclusão.
E então fomos fazer minha função Lambda.
Minha função Lambda executou esse código,
que
estava imprimindo, portanto, registrando
esses eventos.
Portanto, o que eu preciso que
você faça é acessar os logs
do CloudWatch e verificar se vimos
ou não esses logs informativos.
E aqui temos algumas informações sobre
esse fluxo de registro.
E, como você pode ver nesse fluxo
de registro, você obtém muitas
informações.
Certo, então temos uma linha.
Portanto, essa foi uma modificação e
esses foram os registros do DynamoDB.
Portanto, ele fornece a chave, o ID
do usuário e a nova imagem.
Está bem.
E o conteúdo, para que possamos ver
sim, uma segunda edição do post "yay".
E também podemos ver a imagem
antiga do que era antes.
Então, isso foi como uma
solicitação, depois temos uma inserção.
E assim, mais uma vez, podemos ver o
registro do DynamoDB nele.
E, em seguida, a nova imagem e a imagem
antiga não existem porque, obviamente, não
fomos inseridos.
Portanto, não havia nada antes.
E então conseguimos uma remoção.
E, novamente, essa operação de remoção foi
registrada.
Temos a imagem antiga e, obviamente, não
há
uma nova imagem porque a coisa foi
removida.
Está bem.
Portanto, isso é bastante fácil.
Nós apenas ativamos o fluxo e você
foi para a função Lambda e a
função Lambda estava registrando-o, mas
essa é
a base para ter esses tipos
de integrações com fluxos do DynamoDB.
Está bem.
Por fim, certifique-se de desativar o
acionador.
Portanto, no DynamoDB, você pega esse
acionador
e o desativa ou exclui, o
que quiser, e está tudo pronto.
Então é isso para esta palestra.
Espero que você tenha gostado.
E eu o verei na próxima palestra.
