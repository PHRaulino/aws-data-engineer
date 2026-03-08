Então, vamos criar um alarme.
Então, antes de mais nada, vou criar uma instância do EC2 rapidamente.
E vamos criar um alarme em cima da utilização da CPU.
Então, vamos em frente e criaremos uma instância EC2 do tipo T2 micro. Vou digitar rapidamente review e launch e,
em seguida, dizer yes, I have this.
Portanto, não precisamos de um par de chaves ou algo do gênero.
Queremos apenas que a instância seja iniciada.
E a ideia é criar um alarme que encerrará a instância se a CPU chegar
a 100%.
Então, vamos criar esse alarme.
Portanto, precisamos selecionar uma métrica.
Portanto, para isso, precisamos escolher uma métrica.
Portanto, precisamos encontrar nossa instância do EC2.
Portanto, este é o nosso ID de instância aqui e procure por ele.
E talvez eu seja um pouco rápido demais, ok.
Portanto, vamos aguardar o lançamento da instância.
Entrarei na métrica do EC2 por instância e esperarei que ela seja preenchida.
Portanto, demorou cerca de cinco minutos para que algumas métricas aparecessem em meu painel do CloudWatch para minha instância.
Portanto, agora eu provavelmente posso atualizar esta página e terei a chance de encontrar as métricas que estou procurando.
Então, deixe-me selecionar uma métrica e colar a instância em perfeito.
Eu o tenho e vou procurar a utilização da CPU da minha instância.
Portanto, essa métrica está bem aqui.
Selecionaremos essa métrica.
Como podemos ver, temos isso aqui.
E então podemos escolher uma maneira de calcular essa métrica.
Portanto, a soma média, o máximo e assim por diante, o período em que queremos avaliar esse alarme.
Portanto, cinco minutos é bom porque essa métrica é preenchida a cada cinco minutos.
Se não habilitarmos o monitoramento detalhado agora, teremos algumas condições em termos de limite.
Portanto, trata-se de detecção estática ou de detecção de anomalias.
É maior que igual a e assim por diante.
Então, eu diria, por exemplo, que se você for maior que 95% por um longo período.
Portanto, para e aqui você pode dizer três de três.
Isso significa que, por 15 minutos, você fica preso em 95%.
Então, provavelmente há algo errado com essa máquina.
Nesse caso, eu poderia escolher uma notificação, uma ação de dimensionamento automático, uma ação
de EC2 ou uma ação de gerenciador de sistemas.
Mas vou escolher uma ação EC2, ok.
E eu direi, ei, se você estiver em alarme, tudo bem, então encerre essa instância, porque
talvez eu saiba que meu aplicativo às vezes tem uma falha enorme e a utilização da CPU estará em 95% ou 100% por muito tempo.
E a única maneira de resolver isso é simplesmente encerrar a instância.
Portanto, escolherei essa opção e, em seguida, clicarei em next e direi terminate.
Você vê isso em uma CPU alta.
Clique em next (próximo) para verificar tudo e estamos prontos para começar.
Portanto, agora esse alarme obviamente tem dados insuficientes.
Portanto, precisamos esperar 15 minutos para que tudo fique bem.
E ele não será acionado a menos que o façamos.
Assim, poderíamos acessar a instância do EC2 e iniciar uma maneira de aumentar a CPU por 15 minutos.
Mas isso seria muito, muito longo.
Ou podemos usar a chamada de API denominada set alarm states para realmente ver o que aconteceria se esse alarme entrasse
na fase de violação.
Então, vamos dar uma olhada.
Esse é o histórico do alarme, ok.
E o que vou fazer é definir o estado do alarme.
Então, digitei CloudWatch set alarm state.
E vamos dar uma olhada na referência da API.
Portanto, precisamos definir o estado do alarme.
O nome do alarme, o valor do estado e o motivo do estado.
Assim faremos.
Aqui.
Portanto, o AWS CloudWatch definiu o status do alarme.
E então precisamos definir vários parâmetros.
Portanto, o nome do alarme será.
Este aqui.
Em seguida, o alarme.
Portanto, o valor do estado.
Será o alarme e o motivo do estado será o teste.
Pressionamos enter.
E agora esse alarme se atualizarmos a página.
Está agora no estado de alarme.
Como você pode ver, ele diz em alarme.
Portanto, a ação ocorre quando um alarme encerra a instância.
Portanto, se você observar o histórico, verá que o alarme foi atualizado de ok para um alarme.
Em seguida, uma ação foi realizada e executada com sucesso, a ação para encerrar minha instância do EC2.
Portanto, se eu acessar minhas instâncias do EC2 aqui e atualizá-las, como você pode ver, elas
estão sendo encerradas porque houve um alarme que foi acionado sobre essa instância do EC2.
E nós configuramos o alarme para realizar essa ação específica.
Então é isso.
Espero que você tenha gostado.
Espero que isso faça sentido para você e nos veremos na próxima palestra.
