- Certo, então nesta palestra, se
quero lhe dar um pouco de detalhes sobre como ela funciona
em alto nível.
Então, primeiro vamos falar sobre a criptografia
em voo, que será chamada de TLS ou SSL.
O TLS é a versão mais recente do SSL.
Portanto, o que temos é que os dados serão criptografados
antes de serem enviados.
Em seguida, ele será descriptografado após o recebimento.
Portanto, isso serve para
a comunicação entre um cliente e um servidor em uma rede.
Portanto, o que vai acontecer
é que, para criptografar os dados,
serão usados certificados TLS.
E é isso que você vê quando entra em sites e está
escrito HTTPS, o que significa que a conexão entre
você e o servidor será
criptografada usando certificados TLS.
Por que queremos criptografia durante o voo?
Bem, porque estamos enviando dados por uma rede e,
às vezes, por uma rede pública,
e os dados passam por muitos servidores diferentes.
Não queremos ter ataques do tipo "man in the middle", em
que um servidor intermediário recebe os dados
e apenas observa os pacotes que estamos enviando ao servidor.
Portanto, o que queremos é ter HTTPS ou TLS ou SSL, quando sabemos que
somente o servidor de destino pode descriptografar os
dados criptografados que estamos enviando.
Então, vamos dar um exemplo.
Temos um cliente e um servidor
e queremos poder fazer login com segurança
no servidor fornecendo nosso nome de usuário e senha.
Mas queremos apenas que o servidor de destino possa recebê-lo.
Portanto, teremos o nome de usuário e a senha e,
em seguida, aplicaremos automaticamente a
criptografia TLS no lado do cliente.
Os dados serão criptografados e enviados pela rede.
Portanto, como você pode ver, nenhum servidor intermediário pode
descriptografar os dados e somente
o servidor de destino pode usar o mecanismo de descriptografia
TLS para descriptografar esse pacote
e ver que enviamos o nome de usuário e a senha.
E, portanto, dizemos que estamos conectados com segurança.
Portanto, isso é para criptografia em voo.
A próxima é sobre a criptografia do lado do servidor em repouso.
A ideia é que os dados sejam criptografados após
serem recebidos pelo servidor para que sejam
armazenados com segurança.
Em seguida, ele será descriptografado
antes de ser enviado de volta aos nossos clientes.
Ele será armazenado em um formato criptografado
graças a uma chave, e essa chave geralmente é uma chave de dados.
Portanto, toda a ideia de gerenciar essas chaves
para criptografia e descriptografia
é que o gerenciamento deve ocorrer em
algum lugar e o servidor deve ter acesso a essas chaves.
Então, vamos usar um serviço,
por exemplo, o Amazon S3.
Estamos enviando um objeto por HTTP, talvez
até HTTPS para criptografia durante o voo.
Assim, o serviço recebe nosso objeto, mas ele é descriptografado.
Portanto, o serviço pode usar uma chave de dados e,
usando a chave de dados e os objetos descriptografados,
podemos ter a criptografia desse objeto em repouso.
E quando se trata de enviar de volta esse objeto para os clientes,
os objetos criptografados e a chave de dados serão usados
juntos para descriptografar.
Teremos uma forma descriptografada de objeto
e, em seguida, esse objeto será enviado por HTTPS de volta
aos clientes.
Portanto, recebemos o objeto descriptografado como está.
Como podemos ver nesse caso,
há uma criptografia do lado do
servidor porque toda a criptografia e
a descriptografia ocorrem no servidor.
Por fim, vamos falar sobre a criptografia no lado do cliente.
E a ideia é que, desta vez,
os dados sejam criptografados e descriptografados no lado do cliente.
E o servidor nunca deve ser capaz de descriptografar os dados
porque, nesse caso, não confiamos em um servidor.
Portanto, para isso, poderíamos aproveitar a criptografia
para esse mecanismo.
Então, vamos dar um exemplo.
O cliente tem um objeto e a chave
de dados dessa vez é do lado do cliente.
E, após a criptografia, obtemos um objeto criptografado.
Esse objeto criptografado pode ser enviado com segurança para qualquer
serviço de armazenamento disponível, um servidor
FTP, Amazon S3, volumes EBS, etc.
E eles serão armazenados de forma criptografada.
Portanto, o servidor inteiro não pode nem mesmo descriptografar o conteúdo dos dados.
Quando recuperamos o conteúdo,
recuperamos o objeto criptografado diretamente.
E se ainda tivermos acesso à chave de dados no local do cliente,
poderemos executar o mecanismo de descriptografia e obter
os objetos descriptografados de volta.
Então, é isso para os três mecanismos de criptografia
que podemos ver na nuvem.
Espero que você tenha gostado.
E eu o verei na próxima palestra.
