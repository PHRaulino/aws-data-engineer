O Lambda é uma ferramenta de processamento de dados sem servidor
que você pode usar.
Vamos falar sobre o que isso significa.
Então, o que é Lambda?
Basicamente, é uma maneira de executar pequenos trechos
de código na nuvem.
Portanto, se você tiver um pouco de código em praticamente
qualquer linguagem que possa imaginar, o Lambda poderá
executá-lo sem que você tenha que
se preocupar com os servidores em que ele será executado.
Portanto, você não precisa provisionar vários
servidores EC2 para executar seu código, o Lambda faz isso
para você, ele pensa na execução real do seu código,
você só pensa no que o próprio código faz.
Portanto, é um método sem servidor de executar
pequenos trechos de código que serão escalonados
continuamente sem que você precise
fazer nada.
O Lambda dimensionará automaticamente o hardware em que está sendo executado,
conforme necessário, dependendo da quantidade
de dados que está chegando a ele.
Assim, você pode ver como isso se encaixa em um mundo de big data.
Se houver muitos dados fluindo, o Lambda
será automaticamente escalado para cima e para baixo
para lidar com o processamento desses dados de forma dinâmica.
No contexto do big data, ele é frequentemente usado para processar
dados à medida que são transferidos de um serviço para outro.
Portanto, alguns serviços não se comunicam
diretamente com outros serviços no AWS, mas
o Lambda pode ser usado como uma cola
entre praticamente tudo.
Portanto, ele pode ficar lá e ser acionado
por algum outro serviço que envie dados para
ele, como um fluxo de dados do Kinesis, reformatar
essas informações em um formato exigido por algum
outro serviço, enviar esses dados para outro
serviço para processamento adicional e talvez recuperar
esses dados e enviá-los de volta.
Portanto, o Lambda é apenas uma forma de executar
pequenos trechos de código sem estado na nuvem,
que geralmente são usados para unir diferentes serviços
em big data.
Vamos dar uma olhada em um exemplo.
Um uso muito comum do Lambda
é o uso de um site sem servidor
e, na verdade, é possível criar um site sem ter
nenhum servidor que você gerencie,
isso é chamado de site sem servidor e
você pode fazer isso com
o AWS Lambda.
Normalmente, não é possível fazer
isso com um site realmente dinâmico,
mas se você puder criar seu site apenas com HTML estático e chamadas Ajax
incorporadas a esse HTML, bem, você poderá servir
isso a partir do S3 ou algo assim.
E então as chamadas Ajax são tudo com que você precisa lidar.
Então, talvez você tenha um API Gateway na
Amazon que serve como uma espécie de parede entre
os clientes externos e você, o interior do seu sistema.
Digamos, por exemplo, que você
tenha um site no qual alguém precisa fazer login.
Essa solicitação de login pode passar
pelo API Gateway, que, por sua vez, seria enviado ao AWS Lambda.
O Lambda diria,
ok, o site quer que essa pessoa faça login.
Ele pode se virar e criar uma solicitação ao Amazon Cognito
para dizer: você autentica esse usuário ou não?
O Amazon Cognito retornará
e dirá: "Claro, aqui está o seu token".
O Lambda poderia então formatar esse
resultado e enviá-lo de volta ao site.
Portanto, o Lambda é
uma espécie de cola entre a API do site e o Cognito no back-end.
Da mesma forma, digamos que estejamos
criando um aplicativo de bate-papo em nosso front-end.
Talvez precisemos recuperar o histórico de
bate-papo para esse ID de usuário depois que ele fizer login.
Portanto, novamente, o API Gateway receberia essa solicitação.
O Lambda seria acionado por essa solicitação de API e diria,
ok, preciso obter o histórico de bate-papo para esse ID de usuário.
Como faço para criar essa solicitação no DynamoDB?
Em seguida, ele se voltaria, faria a solicitação ao DynamoDB
para obter o histórico do bate-papo, conversaria com o DynamoDB
para obtê-lo e o enviaria de volta ao site por
meio do API Gateway.
Portanto, aqui você vê que o Lambda geralmente desempenha
um papel como uma espécie de cola entre diferentes serviços.
É exatamente assim que vamos
usá-lo em nosso próprio aplicativo aqui.
Em breve, vamos desenvolvê-lo.
Você deve se lembrar que, em nosso aplicativo
de histórico de pedidos, usamos anteriormente um aplicativo de consumidor
do Kinesis em execução em um host EC2 para servir como uma espécie de
cola entre os fluxos de dados do Kinesis e o Amazon DynamoDB.
Agora, não queremos ter que gerenciar servidores
EC2 para uma tarefa tão simples como essa; em vez disso, podemos usar o Lambda, que é uma
opção muito melhor.
Portanto, vamos criar uma função
Lambda que, na verdade, fica entre o nosso fluxo
de dados que está recebendo os registros do servidor
e o DynamoDB, onde queremos armazenar esses dados
a longo prazo.
O Lambda ficará sentado esperando por disparos de
eventos do fluxo de dados,
e cada evento de disparo terá, na verdade,
um lote de eventos que ele precisará
percorrer e extrair cada registro individual
e, em seguida, voltar e gravar isso no DynamoDB.
Então, novamente, o Lambda é apenas a
cola entre o fluxo de dados e algum outro serviço,
neste caso, o DynamoDB.
Mais adiante no curso, criaremos
um alarme de taxa de transação, cuja única
finalidade é nos notificar quando algo incomum
estiver acontecendo em nosso sistema.
Portanto, neste caso, temos um fluxo de dados
do Kinesis que está recebendo eventos e diz que algo estranho está acontecendo
e requer a atenção de alguém.
O Lambda será acionado por esses eventos de fluxo
de dados e, em seguida, criará uma solicitação de SNS
para enviar uma mensagem ao seu celular, notificando-o
de que algo requer sua atenção.
Portanto, mais uma vez, o Lambda é a
cola entre dois serviços diferentes
que não se comunicam diretamente entre si, mas como o
Lambda é apenas código, ele pode fazer qualquer coisa.
Ele pode transformar esses dados de qualquer maneira,
pode se comunicar com qualquer serviço no back-end que você possa
imaginar, pode fazer o que você quiser.
Portanto, é uma espécie de cola mágica
que permite que você junte diferentes componentes de
maneiras criativas, e este é apenas um exemplo disso.
