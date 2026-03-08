sem realmente saber.
É o EC2, e o EC2 tem um bom papel no Big Data, especialmente por trás
dos modos de lançamento.
Já conhecíamos as instâncias On-Demand, Spot e Reserved, mas vamos fazer
uma revisão rápida novamente.
Portanto, o Spot significa que será
uma instância muito, muito barata,
mas a AWS pode tirá-la de você a qualquer momento.
Portanto, você precisa ser capaz de tolerar a perda de instância.
Isso significa que, normalmente, se você
usa Big Data com instâncias Spot,
é necessário haver algum tipo de recurso de checkpointing.
Portanto, o algoritmo de aprendizado de máquina, o Spark, o Hive, todos esses elementos
foram criados para tolerar perdas.
Portanto, eles seriam ótimos candidatos
para executar seus trabalhos de processamento
de Big Data ou seus trabalhos de aprendizado de máquina em instâncias Spot.
Da mesma forma, se você tiver um cluster ou um banco de
dados em execução há
muito tempo, como um cluster de EMR em execução há
mais de um ano ou um banco de dados RDS em execução há mais
de um ano, precisará começar a reservar suas instâncias,
pois, ao reservar suas instâncias com antecedência,
você obterá um enorme desconto.
Portanto, isso é para
coisas que serão muito estáveis ao longo do tempo.
Por fim, para todas as cargas de trabalho
restantes que não sabemos se poderemos
perder, ou não sabemos se poderemos usar por um ano continuamente,
o On-Demand será o tipo de lançamento de instância que desejamos.
Além disso, vamos falar sobre o Auto Scaling.
Portanto, o Auto Scaling pode ser aproveitado para EMR ou outros serviços.
Ele é automatizado para DynamoDB, Auto Scaling Groups, etc.
Isso pode ser muito
útil caso você obtenha mais dados
ao longo do tempo ou se forem dados
sazonais ou diários.
Talvez você receba mais carga
durante o dia e menos carga à noite.
A escala automática pode ser muito útil para isso.
E se você combinar o Auto Scaling com o On-Demand, Spot, isso poderá
lhe proporcionar algumas vantagens realmente
boas em termos de preço e custo.
Por fim, o EC2 está por trás de seu cluster EMR.
Portanto, pense no tipo de nós que
você atribuirá aos seus nós mestres e no
tipo de nós para os seus nós de computação.
Portanto, lembre-se de que os nós de computação
contêm os dados, e os nós de tarefas não contêm dados.
Eles estão aqui apenas para fazer tarefas, ok, então
é isso para o EC2.
Foi apenas uma rápida revisão,
mas esperamos que você tenha uma ideia melhor
de como o EC2 se encaixa no ecossistema de Big Data.
Eu o verei na próxima palestra.
