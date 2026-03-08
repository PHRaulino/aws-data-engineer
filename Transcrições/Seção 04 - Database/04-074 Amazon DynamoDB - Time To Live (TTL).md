Então, agora vamos falar sobre o Time To Live.
após um registro de data e hora expirado.
Portanto, a ideia é que você tenha
uma coluna que definirá e, quando
disser que a hora de agora ultrapassa o valor dessa coluna,
remova o item.
Portanto, o fato de um item ser excluído por uma restrição
de Time To Live não consome nenhuma WCU, portanto, não
há custo adicional.
E esse registro de data e hora deve ser um número
que represente o valor do registro de data e hora da época do Unix.
Como veremos no hands-on.
E os itens expirados são excluídos
dentro de alguns dias após a expiração.
Portanto, se olharmos para uma tabela,
por exemplo, uma tabela de dados de sessão que
tenha duas colunas, ID de usuário e ID de sessão, queremos adicionar um tempo de
expiração, que será o TTL da nossa tabela.
E vamos definir quando cada sessão expirará.
Agora, o que acontece
é que, quando você vai e há um processo de expiração no DynamoDB, ele
olha para a hora atual e
diz: a hora atual é esta.
E ele marcará, examinará
a tabela e expirará os itens que obviamente terão um tempo
de época TTL menor que o tempo atual.
E, em seguida, o segundo processo fará a varredura
e excluirá esses itens da tabela.
E é assim que o TTL funciona.
Agora, esses itens expirados que não foram excluídos
ainda aparecerão nas leituras, consultas e varreduras.
Portanto, se você não quiser usá-los,
precisará fazer uma filtragem no lado do cliente.
Portanto, pode haver alguns itens
vencidos em suas consultas.
Você precisa esperar até 40 horas para ver a exclusão.
E quando os itens são excluídos, eles também
são excluídos de seus índices.
Portanto, seus índices secundários locais
e seus índices secundários globais.
E uma operação de exclusão
para cada item expirado entra no fluxo do DynamoDB.
Isso significa que qualquer item que
for excluído graças ao TTL estará nesse fluxo
e você poderá recuperá-lo se quiser.
Agora, os casos de uso do TTL seriam para reduzir os dados armazenados,
mantendo apenas os itens atuais
para cumprir as obrigações regulamentares.
Ou, por exemplo, para os dados da
sessão, esse é um caso de uso perfeito do TTL.
Então, vamos dar uma olhada em como
podemos definir um TTL no DynamoDB.
Então, vamos criar uma tabela,
que chamarei de DemoTTL.
Agora, a chave de partição será user_id e não precisamos
de uma chave de classificação no momento.
Ok, vamos manter, vamos personalizar as configurações.
Definiremos as provisões e o escalonamento automático.
Teremos uma RCU e uma WCU e, em seguida,
criaremos essa tabela.
Portanto, minha tabela já foi criada,
e o que vou fazer é adicionar um pouco de dados.
Portanto, vou inserir alguns itens.
Então, vou criar um item.
O ID do usuário é john_123 e, em seguida,
adicionarei um atributo, por exemplo,
o nome será John.
E depois quero ter uma expiração do atributo.
Portanto, expire_on e, essencialmente, não é uma
cadeia de caracteres, será um número.
Portanto, fazemos expire_on e, em
seguida, precisamos fornecer uma data de expiração ao John.
Por isso, eu o chamo de conversor de época on-line.
E vamos pegar o primeiro.
Portanto, é assim que podemos traduzir um carimbo
de data/hora de soon em um carimbo de data/hora de época,
que posso inserir no DynamoDB.
Por exemplo, se eu levar, digamos, cinco minutos a partir
de agora, vamos lá.
E eu faço um registro de data e hora humano,
aqui está o valor da época de cinco minutos a partir de agora.
Então, vou colar isso e clicar em Create Item.
Portanto, esse é um item que foi criado.
E criarei um segundo item.
E este é alice_456 como ID de usuário, enquanto
o nome de Alice será Alice.
E precisamos novamente ter um expire_on e o expire_on,
podemos dizer, por exemplo, uma hora a partir
de agora.
Portanto, teremos 10 aqui
e clicaremos em Human date to Timestamp,
pegaremos isso, colaremos e criaremos o item.
Portanto, agora temos duas linhas em nossa tabela DynamoDB.
E ambos têm um atributo expire_on diferente.
Agora precisamos definir o TTL em nossa tabela.
Portanto, se olharmos para nossa
tabela, veremos que o Time To Live está desativado no momento.
Portanto, o que posso fazer é acessar Additional Settings (Configurações adicionais),
rolar a tela para baixo, procurar Time To Live (Tempo de vida) e clicar em Enable (Ativar).
Agora precisamos dar o nome do atributo TTL.
Então, quais são os dados que quero expirar,
o comentário no qual quero expirar?
Portanto, expire_on
é o nome que dei a esse nome de atributo TTL.
E então poderíamos fazer uma prévia.
Portanto, se você executar uma visualização neste momento,
ela dirá que esses dois itens serão excluídos em uma hora.
Portanto, se pegarmos, por exemplo, a hora de agora,
que está bem aqui, e eu fizer a Visualização
de execução, ele dirá que não há itens que eu queira excluir.
Mas se fizermos uma hora a partir de agora, ou seja, se fizermos,
por exemplo, 10:10 e obtivermos esse registro de data e hora bem
aqui, e o colarmos, Run Preview, somente John será expirado.
E se eu for um pouco depois, ou seja, se eu for para 10:50 e pegar uma data de carimbo
de data/hora humana para o carimbo de data/hora e inserir
isso, executar uma visualização, agora
dois itens serão excluídos.
E você pode especificar um valor de época ou um horário personalizado ou nos próximos
60 minutos, 24 horas ou sete dias, o que é muito
legal para executar algumas simulações.
Portanto, podemos ativar o TTL, e agora o TTL está ativado e, automaticamente,
se eu esperar por uma hora, meus itens
estarão completamente expirados.
Isso é muito legal,
e podemos fazer um gráfico de todos
os itens excluídos nas últimas 24 horas graças a esse recurso aqui.
Portanto, essa é uma métrica do CloudWatch.
Então é isso para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
