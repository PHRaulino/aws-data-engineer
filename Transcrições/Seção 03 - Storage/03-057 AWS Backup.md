Portanto, o AWS Backup é um serviço totalmente gerenciado
e permite que você gerencie e automatize
centralmente os backups em todos os seus
serviços do AWS.
E a lista está ficando cada vez maior a
cada dia que passa.
Portanto, a ideia é que você queira
ter um local central.
Você não quer criar scripts personalizados
nem ter processos manuais.
Você deseja ter uma visão
central de sua estratégia de backup.
Portanto, os serviços de suporte são bastante amplos.
Por exemplo, Amazon EC2, EBS, Amazon S3, RDS e todos os mecanismos
de banco de dados suportados,
Aurora, DynamoDB, DocumentDB, Amazon Neptune, EFS, FSX, incluindo
Lustre, Windows File Server e provavelmente outros.
AWS Storage Gateway,
como o Volume Gateway.
E há mais coisas que podem vir com o tempo, mas não vou necessariamente
atualizar essa palestra
porque, bem, isso não importa.
As ideias para que você entenda o conceito por trás
do backup de banco
de dados e os serviços mais importantes
são mostradas no slide.
Portanto, ele oferece suporte a backups entre regiões.
Isso não significa que você não possa
ter seu backup transferido para outra região para uma estratégia
de recuperação de desastres, tudo em um só
lugar.
E também suporta backups entre contas,
se você estiver usando várias contas
em sua estratégia do AWS.
Portanto, ele oferece suporte à recuperação
pontual para serviços compatíveis, como
o Aurora.
Ele oferece suporte a backups agendados e sob demanda.
Há políticas de backup baseadas em tags para garantir
que você faça backup apenas
dos recursos que tenham sido marcados
com produção.
E você pode criar políticas de backup conhecidas
como Planos de backup.
Você define a frequência, por exemplo,
a cada 12 horas ou semanalmente ou mensalmente
ou qualquer expressão cron que você tenha, a Janela
de backup.
Se você quiser fazer a transição do próprio
backup para o Cold Storage.
Portanto, nunca, ou talvez depois de alguns dias,
algumas semanas, alguns meses ou alguns
anos, e o período de retenção de seu backup.
Portanto, sempre ou em dias, semanas, meses e anos.
Portanto, ele é bastante favorável e abrangente
e suporta a maioria dos serviços, o que
o torna um ótimo complemento para
os serviços da AWS.
Portanto, se dermos uma olhada no AWS Backup, criaremos
um plano de backup, como eu disse, e então
você atribuirá recursos específicos do AWS que são
importantes para você.
Portanto, aqui está uma lista, mas ela pode aumentar.
E, depois de bem feito, automaticamente
seu backup, seus
dados serão copiados para o Amazon S3 em um bucket interno
específico para o AWS Backup.
E outro recurso que você
precisa conhecer no AWS Backup é o Vault Lock.
Portanto, você aplica uma política de leitura WORM, Write Once
Read Many.
Isso significa que todos os backups
que você armazena no Backup Vault não
podem ser excluídos.
Portanto, a ideia é que você tenha certeza
e possa provar que, graças à política
de bloqueio do cofre, não é possível
excluir seus backups.
E fornece uma camada adicional de defesa
para seus backups contra, por exemplo,
operações de exclusão inadvertidas ou mal-intencionadas ou atualizações
que encurtam ou alteram o período
de retenção.
E mesmo o próprio usuário root não pode excluir
backups quando ativado.
Portanto, ele lhe dá fortes garantias sobre a segurança
de seus backups.
Pronto, isso é tudo o que você precisa
saber sobre o serviço AWS Backup.
Espero que tenham gostado
e nos veremos na próxima palestra.
