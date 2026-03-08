bem recente, assim como o EMR está se tornando sem servidor, o Redshift também está.
O Redshift Serverless também já está disponível.
E isso promete dimensionar e provisionar automaticamente
o cluster do Redshift para sua carga de trabalho.
Portanto, mais uma vez,
você não precisa pensar em quanta capacidade precisa, ele descobrirá isso para você.
A ideia é otimizar seus custos e seu desempenho.
Portanto, como você está pagando apenas
pela capacidade que está realmente
usando, isso deve economizar
algum dinheiro, além de otimizar o desempenho,
pois se você for executar uma consulta
muito exigente de algum tipo, ele poderá dimensioná-la
automaticamente sem que você precise pensar nisso, o que facilita muito
a vida.
Por baixo do capô, ele está usando algum tipo
de aprendizado de máquina sofisticado.
Eles não entram em detalhes sobre
isso, mas o ML para manter o desempenho no que pode ser
uma carga de trabalho variável e esporádica.
Portanto, mesmo que você o esteja atingindo
com consultas ad hoc, ele aprenderá a lidar com isso.
O principal objetivo disso é facilitar a criação
de um cluster Redshift, certo?
Portanto, não preciso mais pensar em capacidade.
Posso simplesmente iniciar o Redshift
e ele calculará automaticamente
a capacidade de que preciso,
e é só isso que me será cobrado, o que é ótimo.
Portanto, se eu quiser criar um pequeno ambiente de desenvolvimento
ou um ambiente de teste, posso fazer isso em
uma pequena página aqui.
Basta ir em frente e configurar meu novo
banco de dados e ele automaticamente me fornecerá
a capacidade de que preciso e nada mais, o que é muito mais fácil.
Se eu quiser fazer apenas uma análise de negócios ad hoc rápida,
criar um cluster rápido, responder a uma pergunta
e sair, também posso fazer isso.
Não é preciso pensar muito sobre isso.
Eles facilitaram muito a configuração do cluster,
o que facilita o uso por outras pessoas e o incentiva
a usá-lo para mais tipos de aplicativos.
Depois de ativá-lo, você
recebe de volta um endpoint sem servidor
de algum tipo e também um URL para se conectar
a ele por meio de JDBC ou ODBC.
Ou, se estiver fazendo apenas uma coisa
ad hoc rápida, poderá usar o editor de consultas no console também.
Como vimos anteriormente,
você não precisa se conectar
a ele externamente se não quiser.
Então, para começar, a única parte difícil
agora é realmente configurar a função
IAM necessária para configurar o
Redshift Serverless.
Portanto, você precisa começar criando manualmente uma função de IAM
que tenha essa política anexada a ela, aqui à direita.
Você precisa ter certeza de que
tem acesso à ação redshift-serverless manualmente.
E tenho certeza de que isso será facilitado no futuro.
Mas, por enquanto, você mesmo precisa configurar essa função de IAM.
Depois de fazer isso, ao configurar
seu novo cluster Redshift
Serverless, tudo o que você precisa fazer
é informar o nome do
banco de dados, as credenciais de usuário
para o usuário administrador, em qual VPC você deseja
executar e quaisquer configurações de criptografia
personalizadas que queira usar.
Por padrão, ele usará apenas
uma chave KMS de propriedade da AWS, o que geralmente é bom, e quaisquer configurações
especiais que você queira para o registro
de auditoria, mas isso é tudo.
Basta preencher uma página com essas
informações e você terá um cluster Redshift Serverless
esperando por você para ser
usado, o que é incrível.
Após o fato, você pode gerenciar instantâneos
e pontos de recuperação mais tarde, depois de criá-los.
Todos eles ainda são suportados.
Assim, você pode ter instantâneos periódicos
dos seus dados e a capacidade de reverter as coisas, sabe,
do dia anterior, ou qualquer
outra coisa, usando pontos de recuperação mais tarde.
Tudo isso ainda está lá.
Vamos falar mais sobre
como o dimensionamento de recursos realmente funciona no Redshift Serverless.
Portanto, como estamos mudando nosso pensamento para o sem servidor,
eles não podem mais nos cobrar em termos de
servidores se não estiverem realmente expondo
o que são esses servidores.
Portanto, em vez disso, eles nos farão
pensar no que chamam de Unidades de Processamento Redshift ou RPUs.
E essa é a nova métrica de faturamento.
Portanto, você paga pelas horas de RPU até o nível por segundo, além de qualquer armazenamento
que esteja usando.
Portanto, o faturamento no Redshift Serverless é baseado em quantas
unidades de processamento do Redshift você está usando por hora,
além de quaisquer taxas de armazenamento associadas.
Portanto, isso é cobrado, você sabe, por gigabyte em unidades de tempo.
Você pode especificar suas RPUs de base.
Assim, da mesma forma que você poderia especificar a capacidade
inicial com o EMR Serverless, a mesma ideia com o Redshift Serverless.
Você pode ajustar sua capacidade básica.
Agora, por padrão, ele será definido como automático,
para que você não precise se preocupar com isso.
Mas se você quiser melhorar o desempenho da consulta
e souber que precisará de
um pouco mais de capacidade para isso desde o início, poderá
dar uma dica.
Você pode dizer que, para começar, quero entre 32 e 512 RPUs como
nível básico em meu cluster sem servidor.
Também posso definir meu máximo de RPUs.
Portanto, se eu quiser garantir que nunca ultrapasse
um determinado consumo de recursos para controlar meu custo, você também
pode fazer isso.
É claro que eles querem que você o use para aumentar
sua taxa de transferência.
Portanto, embora na prática você provavelmente queira usar
RPUs máximas para garantir que não seja cobrado
por mais do que espera.
Você também pode usá-lo para melhorar o rendimento
de um trabalho se achar que o máximo de RPUs está definido como muito baixo.
Mais algumas informações sobre o Redshift Serverless.
Então, basicamente, ele faz tudo o que o Redshift pode
fazer, com algumas exceções.
Os grupos de parâmetros não são compatíveis com o Redshift Serverless.
O gerenciamento de carga de trabalho também não funciona com ele.
Não faria muito sentido se isso acontecesse, certo?
O ponto principal é que
você não precisa pensar muito sobre isso.
Integração com parceiros da AWS, atualmente não compatível
com o Redshift Serverless.
Além disso, as janelas de manutenção
e as faixas de versão não são compatíveis com
o Redshift Serverless.
Isso é um pouco...
Vale a pena falar um pouco sobre isso.
Com o Redshift normal, você tem essas janelas de manutenção,
portanto, sabe quando as atualizações serão aplicadas ao cluster
e pode planejar adequadamente.
Com o Redshift Serverless,
se uma atualização de software estiver sendo implementada no próprio
Redshift, suas conexões serão interrompidas sem nenhum aviso.
Portanto, não há planejamento avançado real para
isso com o Redshift Serverless.
Isso pode ser algo a se pensar
quando estiver decidindo se vai ou não usar isso por enquanto.
Além disso, não há pontos de extremidade
públicos com o Redshift Serverless.
Você deve acessá-lo em uma VPC.
Ele ainda não tornará isso acessível ao público.
Isso pode mudar.
O monitoramento é algo sobre
o qual se fala na documentação do Redshift Serverless e que
também mudou um pouco.
Portanto, há várias exibições diferentes que ele fornece
para fins de monitoramento, como SYS_QUERY_HISTORY,
SYS_LOAD_HISTORY, SYS_SERVERLESS_USAGE e algumas outras.
Eles fazem o que você acha que eles fazem.
Então, basicamente, é um histórico das consultas.
Há também uma visualização detalhada da consulta
se você quiser obter mais informações.
Informações históricas
sobre a carga em seu cluster
sem servidor, o uso desse cluster.
Tudo isso pode ser útil
para solucionar problemas de desempenho.
Talvez você precise incluir...
Talvez seu máximo de RPUs esteja definido como muito baixo, por exemplo,
e essa pode ser uma maneira de descobrir isso.
Além disso, ele publica dados no CloudWatch.
Os registros de conexão e de usuário são ativados por padrão.
Há também dados opcionais de registro de atividades do usuário,
se você quiser publicá-los também.
Isso será publicado no tópico
do AWS Redshift Serverless CloudWatch.
As métricas publicadas no
CloudWatch incluem QueriesCompletedPerSecond,
QueryDuration, QueriesRunning, entre outras.
E você pode dividir isso em várias dimensões,
como o nome do banco de dados, a latência, que é dividida
em curta, média ou longa.
O tipo de consulta e o estágio da consulta.
O estágio da consulta está no momento em que ela é concluída.
Portanto, tudo isso também está disponível para você.
Mas, em resumo, o Redshift Serverless
funciona praticamente da mesma forma que o Redshift.
A única diferença é que você não está pensando na capacidade
subjacente, nos servidores subjacentes.
Ele está fazendo isso por você.
Portanto, em vez de ser cobrado explicitamente pelo uso do servidor,
você está sendo cobrado por RPUs.
E você tem algumas maneiras de controlar isso,
se necessário, incluindo a capacidade básica e máxima de RPU
para o Redshift Serverless.
