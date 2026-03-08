de segurança com o Redshift.
Falaremos muito mais sobre segurança mais adiante
no curso, mas aqui estão algumas coisas que podem aparecer no exame.
Um deles é o problema de usar um módulo de segurança de
hardware, ou um HSM, com o Redshift.
E se você estiver usando um HSM com
o Redshift, precisará usar um certificado de cliente e de servidor
para configurar uma conexão
confiável entre o Redshift e o HSM.
Agora, se você estiver tentando fazer
isso depois do fato, se estiver tentando adicionar um HSM a um cluster Redshift
existente, terá que copiá-lo.
Portanto, se quiser migrar um cluster não criptografado
para um cluster criptografado HSM, você terá
que criar o novo cluster criptografado primeiro e, em seguida,
mover seus dados para esse cluster
criptografado, certo?
Esse é o ponto principal do uso de
um HSM com o Redshift.
Você precisa de um certificado de cliente e de servidor para fazer isso.
Além disso, aqui está uma coisa legal em que você pode usar os comandos
GRANT ou REVOKE no SQL para realmente definir
privilégios de acesso para usuários individuais ou para grupos
de usuários no Redshift.
Portanto, uma maneira fácil de gerenciar permissões no Redshift
é simplesmente dizer algo como "conceder
seleção na tabela foo para bob".
Isso concederia a Bob a permissão para
executar instruções select na tabela chamada Foo.
E você pode fazer coisas como conceder tudo ou conceder drop para
permitir que as pessoas também descartem dados.
Tudo isso pode ser gerenciado individualmente para
um usuário ou grupo usando o comando GRANT, como qualquer
outro comando SQL, ou o comando REVOKE,
se você quiser remover essas permissões.
Portanto, essa é a maneira fundamental de gerenciar
a segurança e as permissões de acesso no Redshift.
