Agora vamos falar sobre o CloudWatch Alarms.
são usados para acionar notificações de qualquer métrica.
E você pode definir alarmes complexos
e em várias opções, como amostragem ou porcentagem ou máximo,
e assim por diante.
O alarme tem três estados: OK,
que significa que não foi acionado; INSUFFICIENT_DATA,
que significa que não há dados suficientes
para que o alarme determine um estado; e ALARM,
que significa que o limite foi ultrapassado e, portanto, uma notificação
será enviada.
O período é o tempo pelo qual você deseja
que o alarme seja avaliado na métrica.
Portanto, pode ser muito, muito curto, muito, muito longo.
E isso também pode se aplicar a métricas de clientes de alta resolução.
Por exemplo, 10 segundos,
30 segundos ou um múltiplo de 60 segundos.
Agora, os alarmes têm três alvos principais.
A primeira são as ações em instâncias do EC2, como
pará-las, encerrá-las, reiniciá-las ou recuperar
qualquer instância.
A segunda é acionar uma ação de dimensionamento automático.
Por exemplo, uma escala para fora ou uma escala para dentro.
E a última é enviar uma notificação para
o serviço SNS, por exemplo, e, a partir do serviço
SNS, podemos conectá-la a uma função Lambda
e fazer com que a função Lambda
faça praticamente tudo o que quisermos com base
na violação de um alarme.
Agora, vamos falar sobre os alarmes compostos,
pois sabemos que os alarmes
do CloudWatch estão em uma única métrica,
mas se você quiser ter várias métricas, precisará
usar os alarmes compostos.
Portanto, como os alarmes compostos estão,
na verdade, monitorando os estados de vários
outros alarmes, cada um deles pode depender
de uma métrica diferente.
Portanto, o Alarme composto
é a ação de combinar todos esses outros alarmes,
e você pode usar as condições E ou OU para poder
ser muito flexível em termos da condição que
está verificando.
Portanto, é muito útil reduzir o ruído
do alarme porque você pode criar Alarmes compostos
complexos e dizer, por exemplo, se a CPU estiver alta
e a rede estiver alta, não me alerte porque só quero
saber quando a CPU estiver alta e a rede estiver
baixa, esse tipo de coisa.
Vamos dar um exemplo: temos uma instância
do EC2 e vamos criar um alarme composto sobre ela.
Portanto, criamos um primeiro
alarme subjacente chamado Alarme A,
que monitorará a CPU da instância do EC2.
Em seguida, você cria o Alarme B, que monitorará
o IOPS da instância do EC2,
e o alarme composto é definido como a junção do Alarme
A e do Alarme B.
Portanto, se o Alarme A estiver em alarme e o Alarme
B estiver em alarme, e isso
é algo que precisamos definir, então o Alarme
composto em si será um alarme e poderá acionar,
por exemplo, uma notificação do SNS.
Portanto, como você pode ver, é possível ser bastante
criativo com os Alarmes compostos.
Então, vamos falar sobre a recuperação de instâncias do EC2.
Portanto, temos as verificações de
status e a verificação de status da
instância, que verificará a máquina virtual EC2.
E temos a verificação do status do
sistema, que verificará o hardware da camada subjacente
da nossa instância do EC2.
E, por fim, a verificação do status do EBS anexado,
que verificará a integridade dos volumes do EBS anexados.
E você pode definir um alarme do CloudWatch para essas verificações, certo?
Portanto, você monitorará uma instância específica do EC2 e,
caso o alarme esteja sendo violado, poderá iniciar
uma recuperação de instância do EC2 para garantir, por
exemplo, que você mova sua instância
do EC2 de um host para outro.
Quando você faz uma recuperação, obtém o mesmo IP privado, público
e elástico, os mesmos metadados e o mesmo grupo de
posicionamento para sua instância.
E você também pode enviar um alerta para o seu tópico SNS para
ser alertado de que a instância do EC2 estava sendo recuperada.
Agora, o alarme de nuvem tem algumas coisas boas.
Para saber isso, em primeiro lugar, como vimos, podemos
criar um alarme em cima de um filtro de métrica
de logs do CloudWatch.
Portanto, lembre-se de que os registros do CloudWatch têm um filtro de métricas, que
é conectado ao CloudWatch Alarm.
E, quando recebermos muitas instâncias de
uma palavra específica, por exemplo, a palavra
erro, faremos um alerta e enviaremos uma mensagem para o Amazon SNS.
Portanto, se você quiser testar
alarmes e notificações, poderá usar uma chamada
da CLI chamada set alarm states.
Isso é útil quando você deseja acionar
um alarme, mesmo que ele não tenha atingido um limite específico,
porque você deseja ver se o
alarme acionado resulta ou não na ação correta
para a sua infraestrutura.
Então é isso para os alarmes, espero que tenham
gostado e nos vemos na próxima palestra para praticarmos um pouco.
