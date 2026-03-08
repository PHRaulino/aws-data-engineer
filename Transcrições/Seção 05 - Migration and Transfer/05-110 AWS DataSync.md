E o DataSync é um serviço
que está aparecendo bastante no exame.
É muito simples, mas você
precisa saber o que ele faz e qual é a sua essência.
Portanto, a ideia, como uma
imagem, é indicar a sincronização dos dados.
Portanto, mova uma grande quantidade de dados para e de lugares.
E esses locais podem ser, por
exemplo, locais no local ou outros locais de nuvem no AWS.
Portanto, você se conectaria ao seu servidor
usando NFS, SMB, HDFS ou outros protocolos, e ele precisa de
um agente para ser executado no local ou na
outra nuvem para fazer essa conexão.
E você pode, por exemplo, fazer outros tipos de migrações.
Por exemplo, você pode mover dados de um serviço do AWS para
outro serviço do AWS.
E isso não requer nenhum agente.
Eu lhe mostrarei o que isso significa.
Portanto, a ideia é que você possa sincronizar dados
com o Amazon S3, incluindo qualquer classe de armazenamento, até mesmo o Glacier.
Amazon EFS, para armazenar em seu sistema de arquivos de
rede, ou Amazon FSx, e ele suporta todos eles.
Agora, as tarefas de replicação não são contínuas.
Eles são programados, portanto,
você pode fazer com que o DataSync seja executado por hora, diariamente ou semanalmente.
Portanto, há um atraso, certo?
Mas os dados serão sincronizados em um cronograma.
Além disso, o DataSync tem a capacidade
de manter as permissões de arquivo e os metadados.
Isso significa segurança e assim por diante.
Isso significa que ele
está em conformidade com o sistema de arquivos POSIX do NFS e com as permissões do SMB.
Isso é muito importante porque, no exame,
essa será a única opção que
preservará os metadados do seu arquivo
ao movê-lo de um local para outro.
Um agente DataSync pode ser bastante eficiente.
Ele pode executar uma tarefa e
usar até 10 gigabits de dados por segundo.
No entanto, se você não quiser maximizar sua rede, poderá
configurar um limite de largura de banda.
Então, vamos dar uma olhada no que isso significa no diagrama.
Portanto, aqui está o caso de uso da sincronização
de seus arquivos locais usando o protocolo
SMB ou NFS no AWS.
E isso pode ser S3, EFS ou FSx.
Portanto, você tem o local e a região do AWS onde o DataSync
está sendo executado.
Portanto, aqui está seu servidor NFS ou SMB.
E o que você precisa fazer é instalar no
local o agente do AWS DataSync e instruí-lo a se conectar
ao seu servidor NFS ou SMB.
Em seguida, o agente DataSync estabelecerá
uma conexão e também se conectará de forma criptografada
ao serviço DataSync.
A partir daí, você pode dizer a ele para ir aonde quiser.
Isso pode ser qualquer classe de armazenamento para
seus buckets do Amazon S3 ou pode ser AWS, EFS ou Amazon FSx.
E a sincronização pode ocorrer
de uma forma, do local para o AWS, mas
você também pode sincronizar do AWS de volta para o local.
É por isso que ele é chamado de DataSync.
Pode funcionar de qualquer maneira.
Agora, às vezes, no exame, dizemos
que queremos usar o DataSync,
mas não temos capacidade de rede para isso.
Portanto, o que você deve pensar
é em usar o dispositivo AWS Snowcone especificamente porque o dispositivo
Snowcone vem com o agente DataSync
pré-instalado.
Portanto, você pode executar o Snowcone no local
e, em seguida, ele extrairá seus dados, executará
os agentes do DataSync e, em seguida, será enviado de volta à sua região
do AWS e sincronizará
seus dados com os recursos de armazenamento do AWS.
Isso serve para mostrar a arquitetura de sincronização
do local para o AWS ou, por exemplo, de outra nuvem para o
AWS usando os agentes DataSync.
Mas você também pode usar o DataSync apenas para sincronizar
entre diferentes serviços de armazenamento do AWS.
Por exemplo, você deseja sincronizar
entre o Amazon S3, o Amazon EFS ou o Amazon
FSx, de volta ao Amazon S3, ao Amazon EFS ou ao Amazon FSx.
E para isso, novamente,
usaremos o serviço AWS DataSync e ele copiará os dados, é claro, mas também os
metadados serão mantidos entre
os diferentes serviços de armazenamento
do AWS, o que é muito importante.
E, novamente, algo que pode surgir no exame.
Portanto, para lembrá-lo, o DataSync pode sincronizar praticamente
tudo, mas não é contínuo.
É uma tarefa agendada que pode ser realizada
de hora em hora, diariamente, semanalmente, e também preservará os metadados
e as permissões de seus arquivos.
E, finalmente, você precisa executar os agentes
DataSync se estiver se conectando a um servidor NFS ou SMB.
Muito bem, isso é tudo para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
