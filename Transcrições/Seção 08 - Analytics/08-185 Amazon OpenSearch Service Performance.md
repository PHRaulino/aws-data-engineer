Algumas observações rápidas sobre a otimização do
desempenho do seu cluster do Amazon OpenSearch.
Um aspecto a ser considerado é a pressão da memória na JVM, e
alguns cenários que podem resultar
nisso são as alocações desequilibradas de shards em seus nós.
Portanto, se você tiver um determinado
conjunto de fragmentos que está fazendo a maior parte
do trabalho e alguns que estão parados sem fazer nada,
isso pode causar pressão de memória nos fragmentos sobrecarregados.
E quando você fica sem memória, coisas
ruins acontecem, certo?
Você começa a trocar a memória para o disco em seus tanques de desempenho.
Muitas vezes, isso pode resultar em problemas de desempenho.
Além disso, ter muitos fragmentos em um cluster
também pode causar problemas.
Uma espécie de verdade fundamental da computação distribuída
é que, às vezes, menos pode ser mais.
O ato de distribuir esse processamento geralmente
exige mais trabalho do que você imagina e, especificamente,
pode exigir muita memória para gerenciar tudo isso.
Portanto, a conclusão de
tudo isso é que, se estiver vendo erros de pressão de memória
da JVM em seus logs, muitas vezes é possível corrigir isso com menos shards
para obter melhor desempenho.
E a maneira de obter menos fragmentos é excluir os índices mais
antigos e não utilizados, se possível.
Portanto, se houver uma maneira de descarregar os dados
do seu cluster em algum arquivo em que você não precise tanto
deles, talvez você possa descarregar os dados da geleira
ou algo assim e excluir os índices associados a esses
dados antigos e não utilizados, essa
pode ser uma boa maneira de contornar
esse erro de pressão de memória da JVM.
Ou talvez você tenha índices que simplesmente não são usados.
Livre-se deles. Isso também ajudará.
Então, sim, apenas uma
observação rápida sobre como evitar o erro de pressão de memória JVM especificamente
no Amazon OpenSearch.
