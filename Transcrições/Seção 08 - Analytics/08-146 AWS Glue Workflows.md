um pouco de tempo aos fluxos de trabalho do Glue.
Acho que o exame vai mencionar muito isso, porque é uma
ferramenta de orquestração, certo?
Portanto, é uma maneira de organizar fluxos de trabalho
maiores, o que é uma grande parte do trabalho de um engenheiro
de dados, mas é uma das muitas ferramentas de orquestração que a AWS oferece.
Portanto, é importante saber não apenas o
que os fluxos de trabalho do Glue podem fazer, mas também
o que eles não podem fazer, porque provavelmente
você será solicitado a escolher entre fluxos de trabalho do Glue e funções de
etapa do AWS, MWAA e outras ferramentas de orquestração alternativas para se adequar
a um determinado caso de uso.
Os fluxos de trabalho do Glue são realmente destinados a fazer coisas dentro do Glue.
Portanto, ele serve para projetar processos ETL
de vários trabalhos e rastreadores que você pode
querer executar em conjunto.
Mas, fundamentalmente, ele está orquestrando coisas
dentro do Glue, e nada mais.
Portanto, é uma ferramenta para realizar fluxos de trabalho mais complexos
dentro do Glue para ETL especificamente, certo?
Não é nada maior do que isso.
Você pode criar esses fluxos de trabalho a partir de blueprints
do AWS Glue no console, graficamente aqui, ou por meio de uma API.
Portanto, neste exemplo que eles fornecem na documentação, você
pode ver que eles definiram um fluxo de trabalho
do Glue para eliminar a duplicação de dados e corrigir números de telefone em paralelo.
E, uma vez que esses dois processos sejam bem-sucedidos, ele
passará a fazer a atualização do esquema.
Portanto, este é um fluxo de trabalho que fará algumas
transformações em paralelo e, quando terminar, canalizará isso para
um esquema atualizado no final.
Portanto, nada muito sofisticado.
Mais uma vez, quero enfatizar que isso serve apenas para
orquestrar operações complexas de ETL usando o Glue.
Ele não vai além disso.
No entanto, há vários acionadores que podem
dar início ao fluxo de trabalho do Glue.
Portanto, é assim que ele se integra
aos outros serviços em seu ambiente mais amplo.
Eles se baseiam no que chamamos de gatilhos.
E um acionador em um fluxo de trabalho iniciará um trabalho
ou um rastreador, ou um acionador poderá ser disparado automaticamente
quando um trabalho ou um rastreador for concluído.
você pode ter um acionador que se baseia em uma programação.
Portanto, assim como uma expressão cronológica,
se você quiser que algo seja executado todos os dias, a cada
hora, uma vez por mês, toda terceira terça-feira, o que quer que seja,
você pode definir uma programação fixa
para o início do fluxo de trabalho do Glue.
Você também pode fazer isso sob
demanda, é claro, por meio do console ou da API.
E você também pode acioná-lo por eventos da ponte de eventos.
Lembre-se de que os fluxos de trabalho do Glue se integram
aos eventos da ponte de eventos, mas nada mais, certo?
Ele pode iniciar em um único evento ou
em um lote de eventos, o que é bastante interessante.
Assim, por exemplo, se eu tiver um novo objeto que chega ao
S3, posso iniciar um fluxo de trabalho imediatamente com base
nesse único objeto, ou posso definir condições de lote que
digam: "Tudo bem, vou esperar até obter esse número de novos
objetos dentro desse intervalo de tempo e só então iniciarei
meu novo fluxo de trabalho", certo?
Dessa forma, posso agrupar as coisas e dizer:
"Ok, tenho uma quantidade suficiente de novos dados aqui",
e provavelmente devo processá-los agora. E, por padrão, essa é uma
janela de lote de 15 minutos, mas,
você sabe, nem aqui nem ali.
Em resumo, esse é o fluxo de trabalho do Glue.
É muito simples, certo, então lembre-se disso.
Não deixe que isso o atrapalhe
no exame, pois não é difícil entender o que ele faz.
Ele apenas orquestra os trabalhos de ETL do Glue.
Você pode iniciá-lo em um cronograma, sob demanda
ou por meio de eventos de ponte de eventos, e é basicamente isso.
