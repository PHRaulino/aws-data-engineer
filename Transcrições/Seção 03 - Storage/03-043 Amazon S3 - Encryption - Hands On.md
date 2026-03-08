Então, vamos praticar a criptografia.
bucket chamado demo-encryption-stephane-v2.
E rolamos a tela para baixo,
vamos deixar isso ligado, deixar isso ligado.
Vamos ativar o controle de versão do bucket.
E, em seguida, na criptografia padrão, como podemos ver, temos
três opções diferentes, mas precisamos
escolher uma criptografia padrão para nossos buckets.
Portanto, vou falar sobre o SSE-S3
agora e, mais tarde, darei uma olhada no SSE-KMS e no DSSE-KMS.
Então, vamos clicar em Create a bucket (Criar um balde).
E agora criamos um bucket
que tem a criptografia padrão ativada.
Portanto, vamos verificar isso fazendo o upload de um objeto.
Então, vamos adicionar um arquivo
e adicionar nosso café. arquivo jpg.
Em seguida, vamos clicar em Upload.
E, como você pode ver agora, posso clicar nesse arquivo e rolar
para baixo, procurar as configurações
de criptografia do lado do servidor.
E, de fato, o arquivo foi criptografado
com criptografia do lado do servidor
com chaves gerenciadas pelo Amazon S3, portanto, SSE-S3.
Também podemos editar o mecanismo de criptografia de um arquivo.
Assim, eu poderia simplesmente clicar em Editar.
E, como você pode ver, se
editarmos a criptografia do lado do servidor, isso
criará uma nova versão do objeto
com a configuração atualizada.
Portanto, é por isso que habilitei o controle de versão
para o meu bucket, para mostrar
a você que uma nova versão do arquivo será criada.
Portanto, vamos alterar a criptografia.
E, para isso, vamos substituir as configurações do bucket para a criptografia
padrão desse único objeto.
Portanto, temos a
opção de usar o SSE-KMS ou o DSSE-KMS.
Portanto, não vou gastar muito tempo com o DSSE-KMS.
São apenas dois níveis de criptografia no KMS.
Portanto, apenas um KMS mais forte.
No momento, usaremos apenas o KMS.
É mais simples e não vai nos custar nenhum dinheiro.
Portanto, usaremos o SSE-KMS como aprendemos.
Em seguida, temos que especificar uma chave KMS.
Portanto, podemos inserir um ARN de chave KMS ou
escolher entre suas próprias chaves KMS.
Portanto, se escolhermos
uma das chaves KMS agora, você deverá ter
apenas uma chave disponível, a chave AWS/S3, que é chamada de chave KMS padrão
para o serviço S3.
Portanto, se você clicar nela, poderemos usar essa chave.
E isso não vai nos custar nenhum dinheiro,
pois essa é a chave padrão do serviço.
Se você criou sua própria chave KMS, ela estará
disponível nessa lista.
Mas a criação de sua própria chave
KMS lhe custará algum dinheiro todos os meses.
Portanto, para
esse fim, usaremos apenas a chave padrão do AWS/S3 KMS.
Vamos salvar as alterações.
Fechamos isso e, agora, se formos para Versões, como
podemos ver, temos duas versões do nosso
arquivo disponíveis no momento.
Portanto, a versão atual, se rolarmos a tela
para baixo e formos para a criptografia
do lado do serviço, como podemos ver, está de fato criptografada
com SSE-KMS com essa chave de criptografia,
que corresponde à chave padrão do AWS/S3 KMS.
Ok, então isso é muito bom.
Em seguida, vamos para essa parte.
Portanto, podemos fazer o mesmo processo carregando um arquivo e, em seguida, adicionaremos
um arquivo, por exemplo, beach. jpg.
E, em Propriedades, encontraremos
a criptografia do lado do servidor.
E aqui podemos especificar
uma chave de criptografia para usar o mecanismo
de criptografia padrão ou substituí-lo por SSE-S3, SSE-KMS ou DSSE-KMS.
Portanto, essa é uma maneira de fazer isso.
E, por fim, vamos dar uma olhada
nas propriedades de criptografia padrão.
Então, vamos rolar a tela
para baixo e encontrar a criptografia padrão.
Vamos editar isso, e aqui temos a opção.
Portanto, podemos ativar SSE-S3, SSE-KMS
como a criptografia padrão ou DSSE-KMS.
Portanto, no caso de usarmos o SSE-KMS, temos
a opção de chave de balde disponível.
Portanto, o objetivo é reduzir o custo
fazendo menos chamadas de API para o AWS KMS.
Portanto, isso é ativado por padrão.
Se usarmos apenas o SSE-S3, essa configuração não será considerada.
Portanto, vimos que
podemos alterar a criptografia padrão aqui.
E você pode me perguntar, bem, o SSE-C está faltando.
Bem, na verdade, ele
está ausente porque o SSE-C só pode ser feito na CLI,
não no console.
Isso significa que você não pode ativar o SSE-C aqui.
E, por fim, para a criptografia do lado do cliente, embora
você tenha que criptografar tudo no lado do cliente,
carregá-lo no AWS e descriptografá-lo no lado do cliente, não é necessário
informar ao AWS que os dados estão criptografados
no lado do cliente.
Portanto, as únicas opções com
as quais você pode lidar no console são SSE-S3, SSE-KMS e DSSE-KMS.
Então é isso, já vimos todas as opções de criptografia no AWS.
Espero que tenham gostado e nos veremos na próxima palestra.
