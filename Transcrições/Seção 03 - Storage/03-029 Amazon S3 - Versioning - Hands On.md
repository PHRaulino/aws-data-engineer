Então, agora vamos brincar com o controle de versão do S3.
uma configuração de controle de versão do bucket.
Vamos editar isso e ativá-lo.
E isso é para habilitar o controle de versão do bucket.
Portanto, todos os arquivos que substituirmos
agora apenas adicionarão versões aos nossos buckets.
Portanto, isso é bom.
Vamos entrar em nossos objetos
e dizer que queremos atualizar nosso site.
Então, vamos voltar e encontrar o URL do site.
Está bem aqui.
Ok, temos "I love coffee",
mas digamos que queremos escrever "I really love coffee",
portanto, vamos voltar ao nosso arquivo.
E vou editar
e dizer que realmente adoro café.
Eu o salvei.
E agora faço o upload desse arquivo novamente.
Portanto, vou adicionar um arquivo e ele será meu índice. html.
E agora temos o conteúdo atualizado nesse arquivo.
Então, se eu fizer o upload.
É bem-sucedido.
Portanto, agora ele foi sobrescrito.
Se eu acessar minha primeira página da Web e atualizá-la,
receberei "Eu realmente adoro café". Mas o que aconteceu
na parte de trás?
Bem, se formos até aqui e
tivermos essa opção "Mostrar versões", mostraremos
o ID da versão real com os arquivos.
Assim, podemos observar algumas coisas.
Primeiro, os arquivos que havíamos carregado antes,
como a praia. jpg e o café. jpg têm um
ID de versão nulo.
Isso ocorre porque eles foram carregados
antes de termos ativado o controle de versão.
Mas esse índice de arquivos. html, como você pode ver, tem duas versões.
Um deles tem ID de versão nula, que é o arquivo que carregamos
antes de ativar o controle de versão.
Mas o arquivo que carregamos agora mesmo tem um ID de versão.
E, portanto, ao atualizar esse arquivo
e carregá-lo em nosso bucket S3, criamos
um novo ID de versão.
Portanto, isso é algo que você só poderá
ver se ativar essa opção.
Portanto, agora, graças ao controle
de versão, podemos reverter nossa página.
Então, temos "Eu realmente amo café",
mas queremos voltar para "Eu amo café". Então, como fazemos isso enquanto clicamos
nesse ID de versão específico? Certo,
certifique-se de que a opção "Mostrar
versões" esteja ativada e, em seguida, vamos excluir.
E aqui temos que excluir um ID de versão específico do
nosso objeto.
Portanto, quando excluímos um ID de versão específico do
nosso objeto, isso é chamado de exclusão permanente.
Portanto, trata-se de uma operação destrutiva, que não pode ser desfeita.
Portanto, se tivermos certeza, digitamos permanently delete (excluir
permanentemente) nesta caixa de texto e clicamos em delete objects (excluir objetos).
E agora, se você voltar, como podemos
ver, estamos de volta com a data anterior do nosso balde.
Portanto, se eu atualizar essa
página, receberei apenas "Eu adoro café". Mas e se desativarmos a opção "Mostrar
versões"?
Portanto, agora temos apenas nossos objetos
e vou pegar este café. jpg, e eu mesmo
o apagarei.
Portanto, desta vez, não excluímos de
fato o ID da versão subjacente,
mas sim adicionamos um marcador de exclusão.
Portanto, ele não exclui de fato o objeto subjacente,
como veremos.
Vamos apenas digitar delete desta vez.
Não é excluir permanentemente, é apenas excluir
e excluímos o objeto.
Perfeito.
Portanto, agora, se dermos uma olhada no nosso balde,
ele se parecerá com o café. O arquivo jpg está pronto.
Mas se clicarmos em "Mostrar versões", veremos que temos um
marcador de exclusão em nosso café. jpg com essa ID de
versão.
E o verdadeiro, o anterior, pelo menos, café. O arquivo jpg ainda está em nossos
buckets, mas está sendo
substituído, pelo menos neste momento, de uma
perspectiva de versão por um marcador de exclusão.
Então, de volta à nossa página da Web, se
eu atualizar essa página e forçá-la, forçando uma
atualização, pressionando Command + Shift + R para forçar uma atualização,
veremos que a imagem não está disponível.
Então, como podemos recuperar essa imagem?
E se eu tentar, por exemplo, abrir essa imagem
em uma nova guia, isso não funcionará.
Recebo a mensagem "404 Not Found. Portanto, para recuperar os objetos
anteriores, posso clicar nesse marcador
de exclusão e excluir o marcador
de exclusão.
Portanto, vou excluir permanentemente esse marcador de exclusão.
E o efeito disso é que ele restaurará a versão
anterior do meu objeto,
que é esta de antes.
Então, voltando à minha página da Web, se eu atualizá-la agora,
poderemos ver que o café. O arquivo jpg está lá.
Assim, você pode brincar com o controle de versão
e adicionar quantas versões de arquivo quiser.
Você pode começar a excluí-los e ver o que acontece.
Mas espero que tenham gostado desta
palestra e nos veremos na próxima.
