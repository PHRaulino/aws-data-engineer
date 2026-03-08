de cache no CloudFront.
Portanto, o CloudFront tem uma origem de
back-end, é claro.
E se você atualizar a origem do backend, os locais de
borda do CloudFront não saberão disso e só receberão
o conteúdo atualizado da origem
do backend, a atualização que você deseja,
quando o TTL do cache tiver expirado.
Mas esse talvez seja um comportamento indesejável para você,
pois deseja que o novo conteúdo seja exibido o mais rápido
possível.
Portanto, o que você pode fazer é forçar uma atualização
total ou parcial do cache.
E, portanto, você elimina todo o TTL ocorrido, presente
em seu cache.
E, para isso, você também executa
o que é chamado de invalidação do CloudFront.
Portanto, você precisa passar algum caminho de arquivo.
Portanto, você pode invalidar todos os arquivos com
uma estrela ou invalidar um caminho
especial, por exemplo, /images/*.
Certo, então como isso funciona?
Bem, digamos que temos uma distribuição do CloudFront,
dois locais de borda.
Cada local de borda tem seu próprio
cache, que contém o índice. html e as imagens diretamente
de sua origem, que é um bucket S3.
E acontece que, por exemplo, o TTL
para esses arquivos é definido como um dia.
Portanto, isso significa que,
em um dia, os locais de borda buscarão novamente esses arquivos para o cache.
Agora, você, como usuário,
administrador, atualizará os arquivos no
bucket do S3.
Você adicionará ou alterará algumas imagens.
Além disso, altere o índice. arquivo html.
E você deseja que essas atualizações sejam refletidas
o mais rápido possível para seus usuários no CloudFront.
Portanto, o que você
pode fazer é invalidar dois caminhos.
O primeiro será o /index. html para invalidar
um arquivo específico.
Em seguida, você invalidará /images/* para remover
todas as imagens do cache em seus
locais de borda.
Assim, o CloudFront dirá aos locais de borda para
invalidar esses arquivos do cache
e eles serão simplesmente removidos do cache.
Agora, da próxima vez que um usuário solicitar, por
exemplo, o índice. html, o CloudFront
encaminhará a solicitação para um local
de borda específico, que perceberá que
o arquivo não está mais em seu cache.
Portanto, o local da borda fará uma solicitação
em sua origem e obterá o índice atualizado e mais recente. html.
Portanto, você viu o valor das invalidações de cache.
Então, é isso.
Espero que tenham gostado e nos veremos na próxima palestra.
