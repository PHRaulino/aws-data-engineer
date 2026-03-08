Vamos nos aprofundar um pouco
essa é uma ferramenta de orquestração muito poderosa e extremamente relevante
para a engenharia de dados.
Portanto, você pode esperar muitas perguntas sobre isso no exame.
Primeiro, um pouco de terminologia.
Portanto, o fluxo de trabalho que você está definindo em suas funções de etapa
é chamado de máquina de estado.
Essa é apenas uma maneira elegante
de dizer que temos um sistema que define vários estados em que
seu pipeline de dados pode estar, e ele se
move entre esses estados de alguma forma, com
base em alguns critérios, certo?
Cada etapa desse fluxo de trabalho é chamada de estado porque
faz parte de uma máquina de estado, certo?
Isso é tudo, apenas algumas terminologias, apenas algumas palavras.
No entanto, há muitos tipos diferentes de estados que
você pode usar com a função de etapa da AWS.
Portanto, é importante conhecê-las.
O mais útil é o estado da tarefa.
Então, esse é um estado em sua máquina de estado de função de
etapa que faz algo certo?
Talvez ele inicie uma função lambda, talvez
inicie algum outro serviço do AWS para
transformar seus dados, movê-los,
carregá-los ou o que for necessário.
Talvez ele até fale com APIs de terceiros
para fazer algo externo ao AWS.
De qualquer forma, essa é uma nota de tarefa.
Ele está realizando algum tipo de operação real em
seus dados à medida que você avança.
Há também um estado de escolha, que adiciona
lógica condicional por meio de regras de escolha.
Podem ser coisas como comparações.
Se meus dados forem maiores que essa quantidade, talvez
eu faça algo especial com eles.
Se esses dados contiverem informações de identificação pessoal ou algo assim,
talvez eu faça algo especial com eles, certo?
Portanto, os estados de escolha são apenas uma oportunidade
de aplicar a lógica condicional.
Há também um estado de espera que
pode ser usado apenas para atrasar a máquina de
estado por um período de tempo específico.
Se, por qualquer motivo, você quiser dar às coisas,
sabe, tempo para se atualizarem,
é uma maneira um pouco complicada
de fazer isso, mas você também pode incluir um atraso de tempo
nas funções de etapa com um estado de espera.
Há também o estado paralelo, que permite
que você faça coisas separadas em paralelo e ramificações
de execução separadas.
Portanto, um estado paralelo não é, bem,
é um conceito meio confuso de estado, certo?
Na verdade, ele está dizendo que vou criar muitos
estados funcionando em paralelo neste momento.
Assim, posso ter coisas diferentes acontecendo ao mesmo tempo quando
chego a um estado paralelo.
Agora, há também o estado do mapa, então
isso pode ficar confuso.
Isso é algo que você provavelmente deve lembrar.
Portanto, um mapa também é executado em paralelo, mas
ele diz: "Vou executar o seguinte conjunto de etapas
para cada item em um conjunto de dados em paralelo. Portanto, isso é especialmente relevante
para a engenharia de dados, pois é feito
especificamente para operar com dados.
Ele será capaz de trabalhar com arquivos JSON, objetos S3,
arquivos CSV, o que quer que você tenha.
Mas ele vai adotar um conjunto de etapas
e aplicá-las a esse conjunto de dados em paralelo.
Portanto, lembre-se de que uma operação de mapa
dividirá as coisas em processamento paralelo
em seus dados, assim como o Apache Spark ou qualquer
outra coisa, e ela será executada
em paralelo sem precisar de um estado paralelo separado
na frente dela.
Portanto, há um pouco de confusão
entre os estados paralelos e os estados do mapa.
O paralelo é usado para iniciar ramificações separadas
dentro da máquina de estado que podem fazer
qualquer coisa, mas o mapa trata especificamente
de operar nos dados de forma paralela.
Por fim, há o Pass, Succeed e Fail.
O Pass apenas passa seus dados para a próxima etapa. Normalmente,
é usado apenas para depuração.
No entanto, o sucesso e o fracasso são onde você vai acabar.
Assim, uma vez concluída a máquina de estado,
ou você tem sucesso com essa máquina de estado ou falha,
e é assim que você encerra as coisas.
Portanto, essa etapa funciona com um pouco mais de detalhes.
Lembre-se de quais são os tipos válidos de estados
e o que eles fazem, pois isso pode ser útil.
