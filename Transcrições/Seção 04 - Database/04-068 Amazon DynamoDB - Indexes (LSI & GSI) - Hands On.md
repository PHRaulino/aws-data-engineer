Então, vamos dar
uma olhada em como podemos criar índices.
Então, de volta às minhas tabelas, vou criar uma nova tabela,
que chamarei de demo_indexes.
E precisamos escolher uma chave de partição,
portanto, vamos escolher user_id.
E uma chave de classificação, game_timestamp.
Portanto, isso nos permite consultar
E, para isso, vou personalizar as configurações.
Vou dizer que quero a capacidade
provisionada de um grau RCU e um grau WCU.
E aqui podemos definir nossos índices secundários.
Como você pode ver,
podemos criar um índice local ou um índice global.
Agora, os índices locais só podem ser criados no
momento da criação da tabela,
enquanto os índices globais podem ser criados posteriormente.
Portanto, podemos criar um índice local.
E aqui precisamos especificar uma chave de classificação diferente.
Portanto, como você pode
ver, não temos a opção de especificar uma
chave de partição diferente, de modo que user_id
continuará sendo a chave de partição para esse índice, mas podemos especificar
uma chave de classificação diferente.
Por exemplo, digamos
que eu queira criar um índice local
e que a chave Sort se chame game_id.
Portanto, agora o nome do índice é game_id_index.
E quais atributos queremos
projetar nesse índice?
Queremos todos, somente as chaves ou
somente Incluir nomes de atributos específicos que especificamos.
Portanto, manteremos a simplicidade e o faremos como All.
Portanto, acabamos de criar esse índice e podemos
ir em frente e criar um índice secundário global
no qual temos a opção de especificar
uma chave de partição diferente e, opcionalmente,
uma chave de classificação diferente, além
de projetar alguns atributos.
Portanto, por enquanto, não vamos criar esse
índice secundário global.
Vamos apenas criar um índice local, certo?
Em seguida, clique em Create table (Criar tabela).
Portanto, minha tabela foi criada e vamos dar
uma olhada em como podemos consultá-la agora mesmo.
Portanto, se eu entrar em Query (Consulta),
como podemos ver, posso consultar uma tabela ou um índice e ter duas opções.
Posso consultar minha demo_indexes, que é minha tabela.
Portanto, posso especificar um user_id e um game_timestamp,
ou posso consultar meu índice e especificar um user_id e
um game_id.
Portanto, como podemos ver, esse índice local me permite consultar
por uma chave de partição diferente, uma chave de classificação
diferente, desculpe-me,
com a mesma chave de partição.
Portanto, vamos voltar aos detalhes da tabela
e acessar a guia Indexes (Índices).
Portanto, como você pode
ver, há um índice secundário local que foi definido.
Portanto, não podemos criar outro.
Portanto, os LSIs precisam ser definidos no momento da criação da tabela,
e não depois, ou como GSIs,
ou seja, índices secundários globais, que podem
ser criados depois.
Assim, poderíamos criar um índice e
inserir uma chave de partição completamente diferente,
por exemplo, game_id, e uma chave de classificação poderia ser, por
exemplo, game_timestamp, certo?
E isso me dá um GSI.
Agora também precisamos criar alguma capacidade para o meu GSS.
Portanto, os índices secundários locais tocam na RCU e na WSU da tabela principal,
ao passo que, para um índice secundário global, você precisa criar
sua própria capacidade de leitura e gravação.
Portanto, copiamos da tabela de base ou personalizamos as configurações e podemos,
novamente, especificar a ativação e desativação do dimensionamento automático.
Portanto, copiaremos da
tabela básica e teremos um e um para RCU e WCUs e, em seguida, os atributos
que queremos projetar.
E, em seguida, esse índice secundário global será criado.
Lembre-se de que, se você consultar muito o
GSI e as gravações forem limitadas, as gravações também
serão limitadas na tabela principal.
Já o LSI apenas se conecta à RCU e à WCU da
mesa principal.
Pronto, meu índice secundário global foi criado.
E o que posso fazer agora é que, se eu voltar aos itens de visualização, poderei
examinar minha tabela e consultar por
game_id-game_timestamp-index.
Portanto, como você pode ver agora,
a chave da partição pode ser consultada por game_id.
E minha chave de classificação é o registro de data e hora do jogo.
Portanto, isso realmente mostra todos os poderes dos índices.
Espero que isso faça
sentido e nos veremos na próxima palestra.
