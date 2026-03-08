Portanto, estamos nessa.
E vou clicar em Get Started para começar a registrar algumas configurações.
Portanto, vamos registrar todos os recursos suportados nessa região.
Mas, se quiser, você pode registrar apenas tipos de recursos específicos. Nesse caso, você pode encontrar categorias
de recursos e, em seguida, tipos de recursos no lado direito.
Mas como quero mostrar a você todos os recursos que posso gravar, vou clicar aqui.
E, além disso, você pode incluir recursos globais, como usuários de IAM, funções de grupo e políticas gerenciadas
pelo cliente.
Lembre-se de que, novamente, a configuração não faz parte do nível gratuito.
Portanto, quanto mais recursos você gravar, mais dinheiro terá que pagar.
Portanto, estou fazendo isso para mostrar tudo a você.
Mas, se você não quiser pagar nada por esse curso, não faça esse curso prático.
Está bem.
Portanto, vamos registrar todos os recursos.
Vamos incluir recursos globais.
E, para registrar toda a configuração do recurso, precisamos criar uma função vinculada ao serviço de configuração.
Então, vamos clicar nele.
Em seguida, todas essas informações serão entregues em um bucket do Amazon S3.
Portanto, vamos criar um balde.
E o nome do balde já está inserido para mim.
Portanto, isso é perfeito.
E então podemos ter um prefixo, se quisermos.
E, por fim, é aqui que os dados serão armazenados.
E, em termos de notificação, podemos transmitir todas as alterações de configuração e notificações para um tópico
do Amazon SNS, se quisermos.
E, mais uma vez, lembre-se de que isso é para tudo em um único tópico, mas não queira fazer isso.
Portanto, deixarei essa opção desmarcada e clicarei na próxima.
Em seguida, encontramos algumas funções de gerenciamento.
Portanto, temos muitas coisas, como você pode ver.
E quero defini-los mais tarde.
Portanto, vou pular essa parte.
Mas você pode dar uma olhada nelas se quiser.
Portanto, clique em next e poderemos revisar a configuração.
Portanto, sim, queremos registrar todos os registros, todos os recursos, inclusive os recursos globais.
E vamos entregar isso em um bucket S3.
E atualmente não definimos nenhuma regra.
Então, vamos clicar em confirmar.
Agora a regra está sendo criada.
O bucket é criado e, em seguida, a configuração é iniciada.
Agora, levará algum tempo para que o config dê uma olhada em tudo na sua conta.
E veja a configuração.
Portanto, vou pausar o vídeo até que isso seja feito.
Então, meus recursos ainda estão sendo descobertos, mas posso ir para os recursos no lado esquerdo.
E, na verdade, veremos que alguns recursos já foram descobertos em minha conta.
Como você pode ver, foram descobertas algumas sub-redes roteáveis, VPCs e assim por diante.
Então, o que posso fazer é examinar o tipo de recurso e procurar, por exemplo, os grupos de segurança do EC2.
E descobrir que sim, meus grupos de segurança estão aqui e, no momento, eles não têm um status de conformidade
porque não definimos nenhum tipo de regra sobre eles.
Então, vamos dar uma olhada, por exemplo, em um desses grupos de segurança do EC2.
E, dentro do grupo, podemos dar uma olhada nas regras aplicadas.
Portanto, atualmente não há.
E podemos examinar a configuração do próprio grupo de segurança.
Está bem.
Também podemos examinar a linha do tempo dos recursos.
E a linha do tempo do recurso lhe dará todos os eventos relacionados a esse recurso.
Portanto, há uma alteração na configuração, que é a configuração inicial bem aqui.
Há também alguns eventos do CloudTrail relacionados ao grupo de segurança.
Por exemplo, autorizar regras de entrada do grupo de segurança, criar configuração de inicialização e criar grupo de segurança,
esse tipo de coisa.
E podemos acessar o CloudTrail para encontrar esses eventos.
Portanto, o que eu quero fazer é descobrir se meus grupos de segurança estão em conformidade ou não.
Portanto, para isso, vamos entrar em regras.
E as regras nos darão a opção de adicionar uma regra.
E podemos adicionar uma regra de gerenciamento da AWS ou criar nossa própria regra personalizada com uma função Lambda.
Portanto, para simplificar, vou adicionar uma regra de gerenciamento da AWS.
E vamos dar uma olhada nas regras que estão acessíveis para nós.
Então, um que eu gosto é, por exemplo, o Ami aprovado pela ID.
Portanto, isso serve para verificar se as instâncias em execução estão em sua conta usando o Ami especificado.
Portanto, se eu clicar nele, por exemplo, e clicar em próximo, o que não está relacionado a grupos de segurança.
Mas quero lhe mostrar apenas uma regra.
Portanto, este verificará se as instâncias em execução do EC2 usarão ou não os Amis especificados.
Assim, você pode acionar isso com base em qualquer alteração de um recurso.
E você também pode especificar todas as instâncias do EC2 aqui.
E temos que especificar um parâmetro para essa regra, que é a lista de todas as IDs aprovadas em nossa
conta.
E isso será usado pelas regras e entradas para descobrir se essa instância do EC2 está ou não
em conformidade.
Mas como ainda não temos muitas instâncias do EC2, não usaremos essa regra.
Portanto, em vez disso, usaremos uma regra de gerenciamento, mas desta vez para SSH.
E isso será aplicado ao nosso grupo de segurança.
Portanto, queremos ter certeza de que não estamos permitindo nenhum tráfego de entrada de qualquer lugar.
Então, vamos clicar em next.
Isso é chamado de SSH restrito.
E o acionador estará em nosso recurso sempre que a configuração for alterada.
Mas, como podemos ver, se definirmos um tipo diferente de regra, ela também poderá ser executada periodicamente.
Portanto, queremos que sempre que o recurso do grupo de segurança seja alterado.
Por favor, avalie essa regra.
Isso se aplica somente aos grupos de segurança do AWS EC2 e não temos parâmetros para essa regra.
Clique em next (próximo) e em Add Rule (adicionar regra).
E agora definimos essa primeira regra.
Então, vamos dar uma olhada.
Portanto, atualmente não está sendo avaliado e não temos nenhuma correção.
Portanto, vamos esperar um pouco até que isso seja feito.
Então, apenas atualizei minha página e, como você pode ver, uma avaliação foi feita automaticamente.
E se olharmos para essa regra, temos sete grupos de segurança, não há seis grupos de segurança aqui que
não estejam em conformidade.
Portanto, se entrarmos em nossos recursos no lado esquerdo.
E vamos filtrar novamente por grupo de segurança EC2.
E dê uma olhada em todos os nossos recursos.
Como podemos ver, alguns deles estão em conformidade e outros não.
Então, se olharmos para um que está em conformidade e um que não está, vamos ver a diferença.
Portanto, este está em conformidade com as normas.
E uma regra foi aplicada a ele.
E, como você pode ver, ele diz conformidade.
Portanto, se eu for gerenciar o recurso.
E observe as regras de entrada.
Aqui.
Como podemos ver, temos apenas uma regra de entrada que não tem uma porta.
Portanto, não há porta 22 aqui.
Portanto, é por isso que está funcionando.
Mas se eu olhar para um recurso que não está em conformidade, por exemplo, este Launch Wizard três, acredito que não estava em conformidade.
Está bem.
E clicamos em Manage Resource (Gerenciar recursos).
Somos levados novamente direto para o console dos grupos de segurança.
E se observarmos a regra de entrada, como podemos ver, a porta 22 no IPv4 de qualquer lugar está sendo aberta.
Portanto, esse é um grande problema.
Portanto, o que posso fazer é excluir essa regra aqui.
E se eu excluir essa regra, isso acionará uma avaliação do meu recurso que deverá torná-lo compatível novamente.
Portanto, vamos excluí-lo e salvar minhas regras.
Portanto, agora meu grupo de segurança foi modificado.
Então, vou encerrar o assunto.
Portanto, este é o meu grupo de segurança não compatível.
E posso entrar na linha do tempo dos recursos para dar uma olhada.
Assim, dentro da linha do tempo do recurso, como podemos ver, ocorre a alteração da configuração.
Em seguida, a regra foi executada e não estava em conformidade.
Agora, alterei mais uma vez a configuração.
Portanto, teremos que esperar um pouco para que a alteração da configuração ocorra aqui,
o que deve acionar a conformidade com a regra.
E espero que agora meu recurso esteja em conformidade.
Então, deixe-me fazer uma pausa e voltar a falar com você.
Por isso, acabei de atualizar minha página.
E, como podemos ver aqui, em 12 de julho, temos um evento do CloudTrail após a conformidade que ocorreu porque eu
revoguei uma regra de entrada de grupo de segurança porque excluí uma regra de entrada.
Isso é verdade.
Em seguida, ele também registrou uma alteração de configuração dizendo que essa regra que tinha a porta 22 foi excluída.
Portanto, from e to estão vazios porque foram excluídos.
E, em seguida, a configuração executou novamente minha regra denominada SSH restrito.
E agora meu recurso está em conformidade.
Isso significa que sim, eu corrigi a conformidade do meu recurso.
Então, posso voltar aqui e dar uma olhada em outro grupo de segurança, por exemplo, este aqui.
E, de acordo com a regra aqui, você pode tomar medidas e gerenciar a remediação.
Portanto, isso é para remediar essa regra.
Portanto, se analisarmos essa regra, teremos uma remediação gerenciada.
E podemos ter remediação manual ou automática.
Nesse caso, você pode especificar um número de novas tentativas e um número de segundos para que elas ocorram.
Está bem.
Portanto, podemos selecionar uma correção manual, por exemplo.
E então você precisa escolher uma ação de remediação.
Portanto, esses são documentos de automação SSM que podemos selecionar.
Portanto, eles são definidos pela AWS.
Mas também podemos criar a nossa própria.
E, por exemplo, podemos excluir um instantâneo ou excluir uma imagem se ela não estiver em conformidade com o que desejamos.
Portanto, cabe a você definir a ação que deseja.
Assim, por exemplo, você poderia dizer "ei, anexe o volume do EBS e aqui estão os limites de taxa com base nos recursos que não estão em conformidade,
os parâmetros de ID do recurso, se você precisar que eles sejam fornecidos para a correção e assim por diante".
Isso não faz nenhum sentido.
Essa ação de remediação.
Certo.
Precisaríamos definir uma ação de correção que faça sentido para a nossa regra.
Mas, como você pode ver, podemos definir a correção automática ou manual, configurá-la e assim por diante.
E também passando alguns parâmetros em torno do próprio documento.
Está bem.
Então é isso para a configuração, espero que você tenha gostado.
E os agregadores servem para agregar várias contas.
E, em seguida, em configurações, você pode dar uma olhada nas configurações que definimos anteriormente, incluindo,
por exemplo, a configuração de todos os dados em um tópico do SNS.
Ou você pode configurar regras de eventos do Amazon CloudWatch no console do CloudWatch ou no console
do EventBridge para interceptar apenas eventos específicos de não conformidade para algumas regras específicas.
Então, digamos que, para esta palestra, espero que você tenha gostado e nos vemos na próxima palestra.
