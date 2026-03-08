Portanto, no Console de cobrança,
no lado esquerdo, você tem seus
orçamentos, e vamos criar um orçamento.
Portanto, agora você tem uma visão simplificada da configuração do orçamento
e pode usar um modelo,
e alguns deles, por exemplo, é o orçamento de gasto zero para notificá-lo
quando você exceder os limites da camada gratuita da AWS.
Você tem o orçamento de custo mensal para criar um orçamento
que o notifica quando você se aproxima ou excede
um orçamento especificado.
E você tem um orçamento de cobertura do Plano de Poupança Diário, que
consiste em criar um orçamento de cobertura para o seu
plano de poupança que o notifica se você ficar abaixo das metas definidas
do seu plano de poupança.
Portanto, esses
modelos são muito simples de definir e,
em seguida, você cria o modelo, mas
não tem todas as opções de orçamento.
Então, vamos para a seção Personalizar e avançado.
E aqui temos todos os diferentes tipos de orçamento.
Portanto, temos orçamento
de custo, orçamento de uso, orçamento de plano de economia e orçamento de reserva.
Portanto, se você optar pelo orçamento
de custos aqui, teremos uma ideia de todos os custos por mês.
E essa é uma das minhas contas reais,
portanto, você pode ver alguns custos reais nela.
Portanto, vamos inserir um nome de orçamento.
Portanto, este é um DemoBudget.
E então você olha para o período do orçamento.
É diário, mensal, trimestral, anual?
Podemos mantê-lo mensal.
E é um orçamento recorrente
ou um orçamento com prazo de validade que expira no final do mês?
Portanto, teremos isso como um orçamento recorrente.
Digamos, por exemplo, que seja um método de orçamento
fixo e que eu insira US$ 30 de valor orçado por mês.
Portanto, parece que em alguns meses
eu estava acima do meu orçamento de US$ 30 e, em
outros meses, estava abaixo.
Portanto, isso é bom para você visualizar
onde está o limite do seu orçamento
e onde estão seus custos reais.
Você também pode filtrar o escopo do orçamento.
Portanto, no momento, ele está em todos os serviços da AWS.
Podemos filtrar usando uma dimensão específica de custo da AWS.
Por exemplo, podemos examinar os serviços e dizer, ok,
por favor, examine apenas as instâncias do EC2 e aplique
esse filtro.
Portanto, aqui vemos que, em alguns meses,
eu tive o custo das instâncias do EC2 e, em outros, zero.
Portanto, podemos literalmente filtrar por serviços.
Seriam instâncias do EC2 ou outro serviço?
Por exemplo, você pode ter o KMS se estiver interessado.
Portanto, serviço de gerenciamento de chaves.
E, novamente, no Cost Explorer, isso refletirá
o filtro no lado direito.
Mas você pode ser ainda mais granular
e ter mais dimensões, como a região, o tipo de instância, o tipo
de uso, as tags, as zonas de disponibilidade
e assim por diante.
Portanto, você tem muitas opções diferentes para seus filtros.
Certo, então vamos ter a região da UE como uma só, e
vamos aplicar esse filtro.
Ok, a seguir temos opções diferentes.
Então, você quer os custos não combinados
ou os custos amortizados ou combinados, bem como
os tipos de cobrança?
Você deseja ver todos eles ou também reembolsos e créditos?
Então, é possível ir em frente.
Assim, temos os valores orçados e podemos
criar alertas orçamentários.
E isso serve para definir quando você deseja ser alertado
com base em seu orçamento.
E, por exemplo, você pode dizer que, quando atingir 80%
dos valores orçados em relação ao valor real, ele será acionado.
E aqui eu provavelmente receberia
um gatilho este mês com base nisso.
E podemos ter destinatários de e-mail para isso.
Portanto, stephane@example. com seria um destinatário.
Além disso, o Amazon SNS alerta se você
quiser enviá-lo para um tópico do SNS ou o Amazon Chatbots se quiser enviá-lo
para o Amazon Chime ou para as
salas de bate-papo do Slack de sua escolha por meio
dos chatbots.
E você pode ter alertas para valores
reais, mas também pode ter alertas para 80% dos
valores orçados da previsão.
Assim, quando parecer que você está no caminho certo
para atingir 80% do valor orçado, você também
receberá um alerta, o que é bom, porque você receberia
o alerta com antecedência e assim por diante.
Portanto, esses são alertas diferentes que você pode definir.
E, novamente, terei um destinatário para isso.
Perfeito. Vamos clicar em Next e Next.
E aqui nós revisamos tudo.
Assim, podemos realmente incluir ações em nossos orçamentos.
Portanto, aqui na quarta etapa,
você pode fazer edições e adicionar uma ação.
Então, sempre que um alerta é acionado, o que acontece?
Portanto, se eu atingir 80% dos meus custos reais, poderemos
adicionar uma ação e essa ação
exigirá permissões de IAM para ser executada.
Portanto, para isso, podemos criar manualmente uma função IAM,
que permitirá que os orçamentos executem as ações especificadas.
Então, vamos criar
uma função, e a função é para um serviço
do AWS, e esse serviço será o Budgets.
E isso permitirá que os orçamentos
criem e gerenciem recursos da AWS em nosso nome.
Vamos clicar em Next.
E, para as políticas de permissão, eu as terei aqui.
Assim, temos ações orçamentárias com o AWS Resource Access.
Portanto, vou adicionar os dois por precaução
e clicar em Next.
Portanto, AWSBudgetActionsRole será o nome da minha função e criaremos
essa função.
Portanto, minha função foi criada
e, de volta aqui, posso atualizá-la, selecionar uma função de IAM e procurar
a AWSBudgetActionsRole.
E agora que a função foi selecionada, qual
ação queremos aplicar?
Então, se atingirmos o limite do orçamento, queremos
anexar uma política de IAM a usuários, grupos ou funções
para restringir o que eles podem fazer, de modo que não possam,
por exemplo, iniciar mais
instâncias do EC2?
Ou você deseja anexar uma política de controle de
serviços às raízes da organização ou a uma UO específica
para proteger o que uma organização inteira ou uma UO pode fazer?
Ou você deseja interromper automaticamente as instâncias
do EC2 ou do RDS porque elas
podem ser fontes de muitos custos.
Portanto, podemos interromper o EC2 ou o RDS em uma região específica.
Portanto, esse é o tipo
de ação que pode ser executada a partir do console do AWS Budgets.
Portanto, por enquanto, não vou tomar nenhuma medida.
Vamos clicar em Next e criar esse orçamento,
mas pelo menos já vimos todas as opções.
Portanto, agora, nesse console, veremos o orçamento em si, o valor,
a previsão e bons gráficos
sobre onde estamos em relação ao orçamento ou onde
estamos em relação à previsão.
Vamos dar uma olhada nos outros orçamentos.
Então, vamos dar uma olhada no orçamento avançado personalizado.
E aqui temos orçamentos de uso.
Assim, podemos dar uma olhada em usos específicos.
Então, se eu rolar a tela para baixo,
posso dar uma olhada no grupo de tipos de uso ou no tipo de uso.
Assim, podemos analisar, por exemplo, o Data Transfer Inter
AZ e ter um orçamento para ele.
Portanto, essas são as mesmas opções.
Em seguida, você pode criar um orçamento novamente e, dessa
vez, será um orçamento de Planos de Poupança.
Assim, podemos acompanhar nosso plano de economia especificado.
Portanto, SavingsPlanDemo,
e aqui podemos rastrear
a utilização do plano de economia para garantir
que estamos utilizando todo ele, ou a cobertura
para garantir que o uso de nossa
instância seja coberto pelo plano de economia
para o que você quiser.
E, em seguida, você também pode definir o escopo para serviços específicos
ou filtrar por dimensões.
E, por fim, temos os orçamentos de reserva,
para o caso de você ter reservas.
Portanto, reservas, que eu não tenho no momento.
Portanto, nesse menu suspenso aqui para Serviço, nada será encontrado.
Mas podemos rastrear, novamente,
um orçamento em relação à utilização de reservas
ou à cobertura de reservas.
Mas, para isso, você precisa ter instâncias reservadas.
Então é isso. Vimos todas as opções de orçamentos.
Espero que tenham gostado e nos veremos na próxima palestra.
