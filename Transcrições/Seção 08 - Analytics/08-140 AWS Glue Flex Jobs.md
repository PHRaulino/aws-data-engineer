Algo que está aparecendo no
exame
ultimamente são os trabalhos do Glue
Flex.
Eles são bem parecidos com o que parecem.
Portanto, trata-se de uma nova classe de
execução chamada FLEX,
que é apropriada para cargas de trabalho
não urgentes.
Portanto, se você não se importar
realmente com a data
de execução do trabalho ou necessariamente
com a capacidade que
ele tem, poderá executar um trabalho Flex
para usar a
capacidade de computação sobressalente em
vez de trabalhadores dedicados.
E, é claro, essa é uma maneira de
economizar dinheiro.
Agora, a desvantagem é que talvez você
tenha que esperar que essa capacidade
fique
disponível ou talvez ela não esteja
disponível, e nesse caso você poderá
obter menos capacidade do que solicitou.
No entanto, se você tiver uma carga de
trabalho com pouco
tempo de duração, talvez esteja fazendo
algum teste, ou uma carga
única, ou algo no fim de semana em que não
se
importe com a data exata de execução,
apenas queira que
ela seja executada em algum momento no
futuro próximo, um
trabalho Flex pode ser uma maneira de
economizar algum dinheiro.
Quanto custa? Normalmente, cerca de 30 a
35%
menos do que um trabalho de execução
padrão.
Você só será cobrado pelo número
real de trabalhadores usados e
pela duração real da operação.
E, novamente, você pode acabar com menos
do
que pediu se a capacidade não estiver
disponível.
No entanto, há algumas ressalvas, de modo
que você não pode
usar trabalhos do Flex com trabalhos de
shell do Python,
com trabalhos de streaming ou com
trabalhos de aprendizado de
máquina do AWS Glue, que podem ser
importantes de lembrar.
Portanto, em resumo, em um nível mais
alto,
se você precisar de recursos dedicados ou
tempos
previsíveis e desempenho previsível ou
SLAs concretos, é
melhor usar um trabalho padrão de cola.
Mas se você estiver disposto a trocar isso
por economizar
algum dinheiro, um trabalho Flex pode ser
para você.
