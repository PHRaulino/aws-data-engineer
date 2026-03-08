Então, vamos praticar
Para isso, vamos criar um novo bucket.
Vou chamá-lo de s3-stephane-bucket-origin-v2.
E eu o definirei em uma região que eu quiser,
por exemplo, eu-west-1.
Esse será meu bucket de origem
e, em seguida, os dados serão
replicados desse bucket para outro bucket.
Portanto, o que preciso fazer, é claro,
é ativar o controle de versão,
pois a replicação só funciona se o controle
de versão estiver ativado.
Portanto, vou criar esse balde.
Em seguida, abra esse balde em uma nova guia.
Criarei um segundo compartimento e esse
será o meu compartimento de destino.
Portanto, usarei o s3-stephane-bucket-replica-v2.
E, desta vez, a região pode ser a mesma,
por exemplo, se você quiser fazer a replicação na mesma
região, ou algo completamente
diferente, por exemplo, se
você quiser os EUA, poderá fazer us-east-1 para
replicar da Europa para os EUA.
Certo, então vamos rolar a tela para
baixo e habilitar novamente o controle de versão
do bucket no bucket de destino.
E estamos prontos para ir.
Portanto, agora temos nosso bucket primário
e nosso bucket secundário.
O que vou fazer é carregar um arquivo
no bucket de origem, portanto,
adicionarei um arquivo da minha praia, por exemplo.
Praia. jpg.
Ok, isso está feito e podemos encerrar o assunto.
Portanto, agora há um arquivo,
mas, é claro, ele ainda não é replicado porque ainda
não configuramos a replicação.
Então, vamos em frente e fazer isso.
Portanto, no bucket de origem,
o que preciso fazer é ir em Gerenciamento, rolar para baixo
e ver as regras de replicação.
Atualmente, zero.
Então, vamos criar nossa primeira regra de replicação.
Portanto, chamarei essa regra de DemoReplicationRule.
Certo, perfeito.
Vamos defini-la como ativada.
Para o bucket de origem, vamos deixá-lo
como está e, em termos de escopo
da regra, vamos aplicá-la a todos os objetos do bucket.
Agora, para o destino,
podemos especificar um bucket nesta conta
ou em outra conta.
E escolheremos um nesta conta.
E o nome do bucket é o meu bucket de destino.
Portanto, preciso digitar o nome.
Então, vamos pegar esse balde
aqui, copiar e colar.
Certo, e como você pode
ver, a região de destino foi identificada
como sendo us-east-1.
Portanto, trata-se de uma replicação entre regiões.
Está bem.
Agora, para a função
IAM, precisamos criar uma nova função para isso.
Portanto, aqui está a opção.
Depois, podemos dar uma olhada em algumas configurações, mas,
por enquanto, isso não é realmente importante para nós.
Vamos salvar isso.
Portanto, recebemos uma solicitação aqui,
que diz: você deseja replicar objetos existentes?
Portanto, acontece que quando você ativa a replicação, ela
só replica os objetos a partir do momento
em que você a define.
Portanto, para uploads mais recentes.
Portanto, se você quiser replicar os objetos anteriores do bucket
de origem para o bucket de destino,
poderá usar algo chamado Batch Operation, uma
Batch Operation do S3 para fazer isso e precisará
dizer sim, replicar objetos existentes.
Mas isso é separado
do recurso de replicação em si.
Portanto, vou dizer não, não
replique objetos existentes.
E estamos prontos para ir.
Então, vamos dar uma olhada.
Portanto, temos esse gerenciamento com
uma regra de replicação que está pronta.
E agora vou verificar
meu balde de réplicas.
É claro que, se eu atualizar agora, veremos
que os objetos não foram replicados.
Portanto, vou fazer o upload de um novo arquivo,
por exemplo, o upload do café. arquivo jpg.
Faça o upload.
Terminamos.
Então, aqui está o café. arquivo jpg.
Vamos mostrar as versões.
Então, isso é café. jpg e a versão é GBk.
Certo, perfeito.
Agora, se formos ao meu bucket de destino e atualizarmos isso,
levará talvez cinco segundos.
E isso levou cerca de 10 segundos na primeira replicação,
mas podemos ver que meu café. jpg foi adicionado
ao meu balde de réplicas.
E se eu mostrar as versões, podemos
ver que o ID da versão do meu café. jpg é exatamente
o mesmo do balde de origem.
Portanto, os IDs da versão são replicados,
o que é ótimo.
E se eu quisesse importar a praia. jpg, eu precisaria
fazer upload de uma nova versão desse arquivo.
Então, vamos fazer o upload da praia. jpg novamente.
Agora que o upload foi
feito, podemos dar
uma olhada nas versões, portanto, há uma nova versão
aqui do DK2 da minha praia. arquivo jpg.
E agora, se eu for aqui e atualizar, vamos dar uma olhada
em mais uma configuração que
é importante para o seu exame.
Portanto, se eu voltar ao Gerenciamento,
pegar e editar essa função, poderemos rolar para baixo
e dar uma olhada em uma configuração
chamada replicação do marcador de exclusão.
Portanto, por padrão, os marcadores de
exclusão não são replicados, mas há
um recurso para fazer isso.
Portanto, se você ativar a replicação de marcadores
de exclusão, eles serão replicados de um bucket para outro.
Então, vamos salvar isso.
Portanto, minhas regras de replicação foram salvas.
Isso significa que, se eu for a esse balde
e optar por excluir esse arquivo,
por exemplo, excluo meu café. jpg, vamos excluí-lo.
Na verdade, isso criará um marcador de exclusão
porque meu bucket é versionado.
Terminamos.
Então agora meu café. jpg é excluído.
E vamos dar uma olhada aqui.
Então, vamos atualizar e precisamos esperar um pouco.
E agora você pode ver que o marcador de
exclusão foi replicado para o meu bucket de réplica.
Portanto, se eu não mostrar a versão,
não verei meu café. jpg, mas é claro que,
se eu mostrar as versões, eu as verei.
Isso é verdade aqui.
E, é claro, isso também é verdade aqui.
Portanto, os marcadores de exclusão
são excluídos, mas se você decidir excluir uma versão específica
de um arquivo, por exemplo, eu excluo
este, ou seja, excluo um ID de versão específico.
Portanto, isso é chamado de exclusão permanente.
E se eu excluir permanentemente um objeto no meu bucket
de origem, ele não será replicado
no meu bucket de réplica.
Portanto, esta praia. O jpg aqui nunca será excluído
porque apenas os marcadores de exclusão são replicados,
não as exclusões, ok?
Então é isso para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
