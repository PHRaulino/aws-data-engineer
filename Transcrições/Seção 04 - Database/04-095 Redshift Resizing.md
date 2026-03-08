não for suficiente e você precisar redimensionar o cluster em tempo
real, ou seja, adicionar mais capacidade a ele?
Bem, há algumas maneiras de fazer isso, e você precisa
entender a diferença entre elas.
Portanto, um deles é chamado de redimensionamento elástico.
Você pode usar isso para adicionar ou remover rapidamente
nós do mesmo tipo.
Portanto, se você estiver satisfeito com o tipo de
nós, o tipo de instâncias do EC2
que estão executando o cluster do Redshift,
poderá adicionar mais ou removê-las usando o redimensionamento elástico.
Com o redimensionamento
elástico, seu cluster ficará inativo por apenas
alguns minutos enquanto ele adiciona
essa capacidade, e ele tenta manter essas
conexões abertas durante o tempo
de inatividade, de modo que talvez você não perca nenhuma
consulta, mas apenas mantenha a conexão aberta e a retome
assim que a capacidade
adicional estiver instalada em seu cluster.
Agora, um limite do redimensionamento elástico é que, para
determinados tipos de nós dc2 e ra3, você está limitado a dobrar ou
reduzir pela metade o tamanho desse cluster.
Você não precisa realmente
se lembrar de quais são os tipos específicos
para o exame, mas para certos tipos, é isso que você precisa fazer, você
só pode dobrá-los ou reduzi-los pela metade.
Se você precisar fazer algo um pouco mais
complexo, precisará voltar ao chamado redimensionamento
clássico, que permite alterar os tipos de nós e/ou
o número de nós.
O problema com o redimensionamento
clássico é que, se você estiver realmente
alterando os tipos de nós, pode levar horas ou até dias
para que o cluster se torne gravável novamente.
Portanto, seu cluster estará em um estado somente de
leitura durante todo o período
de tempo necessário para provisionar o novo hardware
e trocá-lo em seu cluster.
Essa pode ser uma experiência muito longa.
Portanto, você deve usar o redimensionamento elástico
quando puder, mas se precisar alterar o tipo de nó, deverá
usar o redimensionamento clássico.
Essa é a principal diferença.
Uma técnica para lidar com coisas nesse cenário
clássico de redimensionamento é usar
o que chamamos de snapshot, restore, resize.
E essa é uma estratégia para manter seu cluster disponível durante
uma operação clássica de redimensionamento.
Portanto, se você precisar alterar o tipo
de nó ou adicionar uma quantidade de capacidade que
o elastic resize não permita, o que você pode fazer
é usar um comando de snapshot para fazer uma
cópia do cluster e, em seguida, redimensionar
esse novo cluster.
Portanto, seus dados ainda estão indo para o cluster antigo
enquanto o novo cluster está sendo redimensionado
e passando pelo processo clássico de redimensionamento.
Quando o novo cluster estiver concluído,
você poderá transferir seu tráfego
para o novo cluster que foi criado.
Portanto, o snapshot, a restauração e o redimensionamento são uma forma de migrar de um cluster
para outro usando o redimensionamento clássico para minimizar o tempo
de inatividade.
