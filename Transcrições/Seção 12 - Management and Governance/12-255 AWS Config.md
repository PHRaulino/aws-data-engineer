Portanto, a configuração é um serviço que permite que você obtenha auditoria e registre a conformidade dos seus recursos no AWS com
base em algumas regras que você definirá.
Você também pode registrar a configuração e suas alterações ao longo do tempo para poder reverter rapidamente
e descobrir o que aconteceu na sua infraestrutura, se necessário.
Portanto, algumas perguntas que podem ser resolvidas pela configuração são: há um acesso SSH irrestrito aos meus grupos
de segurança ou meus buckets têm algum acesso público?
Ou há uma configuração do Alb que mudou com o tempo?
Em seguida, com base na conformidade ou não dessas regras, você pode receber alertas ou notificações de SNS sobre quaisquer
alterações.
O Config é um serviço por região, portanto, você precisa configurá-lo para todas as regiões, se necessário,
e pode agregar os dados entre regiões e contas para centralizá-los em um único local.
Você também pode armazenar a configuração de todos os seus recursos no Amazon S3 para serem analisados posteriormente, por exemplo,
por um mecanismo de consulta sem servidor, como o Athena.
Então, que tipos de regras entram na configuração?
Bem, você pode ter regras de configuração gerenciadas pelo AWS, e há mais de 75 regras que você pode usar.
Ou você pode criar suas próprias regras de configuração.
E, nesse caso, você mesmo precisa definir essa regra usando uma função lambda.
Por exemplo, você pode avaliar se cada disco do EBS será do tipo GP2 ou se cada instância do EC2 em sua conta
de desenvolvimento será do tipo T2 micro.
Algumas regras podem ser avaliadas ou acionadas sempre que uma configuração for alterada.
Portanto, sempre que, por exemplo, você tiver uma nova configuração do disco do EBS, avalie o tipo do disco do
EBS, ou você também pode fazer com que a regra seja avaliada em intervalos de tempo regulares.
Por exemplo, a cada duas horas.
Certifique-se de que todos os meus discos EBS sejam do tipo GP2.
Agora, as regras de configuração são apenas para conformidade.
Elas não impedem a ocorrência de ações.
Essa não é uma ação de negação de nada.
Ele não substitui os mecanismos de segurança, como o IAM.
Certo, mas o que ele oferece é uma visão geral da sua configuração e da conformidade dos seus recursos.
Agora não há nenhum recurso para configuração.
Isso pode ser bastante caro.
Muito rapidamente você pagará 0. 3 centavos por item de configuração registrado por região e 0. 1 centavo por avaliação de regra
de configuração por região.
Agora, para o recurso de configuração, você poderá visualizar a conformidade de um recurso ao longo do tempo.
Por exemplo, o grupo de segurança não está em conformidade.
Em seguida, você pode visualizar a configuração do recurso de configuração ao longo do tempo.
Está bem.
Você pode ver quando foi alterado, quem o alterou e assim por diante.
E você pode vinculá-lo ao CloudTrail para visualizar as chamadas de API feitas para esse recurso.
Assim, você pode ter uma visão completa de tudo o que está acontecendo.
Agora, embora não seja possível negar a realização de qualquer ação a partir da configuração, você pode fazer correções
dos seus recursos não compatíveis usando um documento de automação do SSM.
Portanto, a ideia é, por exemplo, monitorar se as chaves de acesso expiraram ou não.
Por exemplo, eles têm mais de 90 dias e, nesse caso, você deve marcá-los como não conformes.
Portanto, isso não impedirá que eles não estejam em conformidade.
Mas você pode disparar sempre que um recurso não estiver em conformidade com uma ação de correção.
Por exemplo, há um documento SSM chamado Revoke Unused User credentials (Revogar credenciais de usuário não utilizadas).
Ok, talvez você queira usar este aqui.
E, em seguida, ele será aplicado a qualquer recurso que você tenha, certo?
E, nesse caso, ele desativará suas chaves de acesso ao IAM.
Portanto, a ideia é que, usando documentos gerenciados ou criando seus próprios documentos de automação, você possa ter
correções dos recursos que não estão em conformidade.
Está bem.
E, se você quiser e for até o fim com os scripts, poderá criar um documento que invocará uma
função Lambda e estará livre para fazer o que quiser.
Então, finalmente, sua remediação pode ter uma nova tentativa.
Portanto, caso o recurso ainda não esteja em conformidade após uma correção automática, ele poderá tentar novamente, por
exemplo, até cinco vezes.
Então, Leslie, e quanto às notificações?
Bem, podemos usar o EventBridge para acionar notificações sempre que nossos recursos não estiverem em conformidade.
Assim, por exemplo, monitoramos nosso grupo de segurança.
Ele se torna não compatível.
Em seguida, podemos acionar um evento no EventBridge e passá-lo para o recurso que você quiser.
Ou você também pode transmitir todas as alterações e todas as reclamações que as notificações de seus recursos para
o SNS a partir da configuração.
Portanto, trata-se de um item de configuração única.
E, se você quiser filtrar apenas alguns eventos, poderá usar uma filtragem de SNS para ter um tópico
de SNS filtrado.
E, em seguida, você pode enviar essas notificações, por exemplo, para um e-mail de administrador ou para um canal do Slack e assim
por diante, para receber todas essas notificações em um só lugar.
Então é isso para a configuração.
Espero que você tenha gostado e nos vemos na próxima palestra para colocar a mão na massa.
