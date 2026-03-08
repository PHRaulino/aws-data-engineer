Então, às vezes, um
você deseja modificar o catálogo de dados em si, como
parte disso.
Talvez você tenha adicionado alguns campos ou tabelas ou, como resultado,
tenha mudado um pouco as coisas de lugar.
Então, como fazer isso
quando você tem esse rastreador que
foi executado e que definiu seu esquema?
O que acontece quando você quer
mudar esse esquema, mais tarde, após o fato.
Bem, há algumas maneiras de fazer isso.
Talvez você também precise alterar
o particionamento como parte do ETL.
Você pode optar por armazenar esses dados de forma diferente.
Em diferentes partições.
Além disso, é algo com que você precisa lidar.
Acontece que há algumas maneiras.
Portanto, A, você poderia simplesmente executar novamente o rastreador.
Mas a outra maneira seria
ter seu script ETL.
Na verdade, altere explicitamente as partições usando
as opções ativar catálogo de atualização e chaves
de partição, enquanto estiver configurando
as coisas.
Portanto, é possível fazer isso.
Você também pode atualizar esse esquema de tabela.
Novamente, a opção A é apenas reexecutar o rastreador, mas você
também pode fazer isso a partir de um script, usando
a ativação do catálogo de atualização
e o comportamento de atualização para atualizar o esquema de uma tabela
explicitamente, depois de terminar
o processamento.
Você também pode criar novas tabelas a partir
do seu script.
Novamente, você usaria o enableUpdate Catalog.
E atualize o comportamento para isso.
Juntamente com o conjunto de informações do catálogo,
para criar novas tabelas a
partir do seu script, se necessário.
E há algumas restrições para
fazer todas essas coisas.
Em primeiro lugar, a modificação do catálogo
de dados do ETL só pode ser feita quando
o S3 for seu armazenamento de dados subjacente.
Também está limitado aos
formatos JSON, CSV, Avro e Paurqet.
E se você estiver usando o Parquet,
há um código especial que você
precisa conhecer quando estiver fazendo isso.
Além disso, não há suporte para esquemas aninhados.
Portanto, essas são as pegadinhas ao
modificar seu catálogo de dados.
Mas é importante saber
que o Glue ETL permite que você faça isso.
Não é necessário executar novamente
o rastreador em todos os casos.
Às vezes, seu script
pode realmente adicionar novas partições,
atualizar o esquema da tabela ou até
mesmo criar novas tabelas diretamente
do script.
