Eles parecem estar investindo muito nesse recurso no momento, portanto, não sei se você
verá isso no exame ainda, mas provavelmente verá em breve.
Portanto, um desses novos recursos é chamado de AWS Glue Studio.
Basicamente, trata-se de uma interface visual para definir e criar fluxos de trabalho de ETL.
Assim, ele permite que você crie esses fluxos de trabalho mais complexos, nos quais pode haver várias coisas acontecendo
em paralelo a partir da mesma fonte, ou talvez fontes diferentes sendo processadas em paralelo de maneiras diferentes.
Mas ele permite que você configure esses trabalhos complexos de forma visual e, muitas vezes, sem escrever nenhum código.
Portanto, ele oferece esse editor de trabalho visual que mostrarei em breve e que permite criar gráficos acíclicos
direcionados para fluxos de trabalho complexos como este.
E as fontes disso atualmente podem incluir S3 ou Kinesis ou Kafka ou qualquer fonte JDBC também.
Em seguida, você pode configurar graficamente as transformações desses dados na interface do usuário do Glue Studio.
Portanto, você pode fazer transformações, amostrar os dados, unir tabelas e algumas outras
coisas também.
E, em seguida, você pode pegar a saída dessa transformação e enviá-la para o S3 ou para o catálogo de dados do Glue.
Ele também oferece suporte ao particionamento imediato.
Portanto, se você tiver dados particionados, ele automaticamente tirará proveito disso e se acelerará
de acordo.
Além disso, ele oferece um painel de trabalho visual que permite visualizar o status de seus trabalhos de ETL de cola e como eles estão sendo executados, o que
está sendo executado e quanto tempo estão demorando.
Portanto, isso pode ser útil para a rápida solução de problemas e para garantir que os trabalhos estejam sendo executados conforme o esperado.
Vamos nos aprofundar e mostrar a você como isso realmente funciona.
Então, deixe-me fazer um breve tour pelo Glue Studio.
É um pouco difícil encontrá-lo atualmente, pois em alguns lugares ele é chamado de
Glue Studio e, em outros, de ETL visual.
Você pode chegar lá de várias maneiras.
Uma delas seria a partir deste botão ir para os trabalhos de ETL aqui, ou a partir da pequena barra lateral aqui.
Está em ETL visual, em trabalhos de ETL.
E você pode ver que agora estamos chamando o Glue Studio novamente.
Vamos clicar no botão ETL visual só para mostrar um pouco do que se trata.
E você pode ver que a lista de fontes cresceu consideravelmente ao longo do tempo.
Portanto, não se trata apenas de cola, catálogo de dados, S3, Kinesis e Kafka, mas praticamente qualquer fonte de dados que
você possa imaginar, mesmo que seja fora da Amazon, é um jogo justo.
Portanto.
Portanto, qualquer banco de dados externo, MySQL, Microsoft SQL, qualquer coisa que você possa imaginar, até
mesmo snowflake, Google BigQuery, você sabe, coisas de fornecedores concorrentes, até mesmo Azure, uh, MongoDB, zoom, ferramentas
de terceiros como QuickBooks ou LinkedIn.
Quero dizer, acho que até o Salesforce PayPal está aqui em algum lugar.
A lista continua.
Portanto, praticamente todos os dados que você possa imaginar podem ser usados pelo Glue Studio.
Portanto, começamos adicionando um nó para uma fonte.
Vamos simplificar e dizer que é algo que eu tenho no S3.
Basta clicar no nó da fonte de dados e informar onde ela está.
Então, vou escolher uma das fontes de dados que tínhamos anteriormente no curso, em registros de pedidos.
Registros de pedidos Sundog soft.
Portanto, é aí que esses dados estão chegando.
E agora, se olharmos para o esquema de saída, ele me dirá como são esses dados.
Portanto, agora podemos fazer coisas para transformar esses dados.
Vamos clicar nele, clicar em mais e adicionar um nó de transformação.
E você pode ver que há muitas coisas diferentes que você pode fazer aqui também.
Portanto, podemos alterar o esquema de consultas SQL, filtros, excrementos e outras coisas.
Deve haver até mesmo alguns recursos para escrever seu próprio código personalizado em algum lugar.
Sim, é isso mesmo.
Transformação personalizada.
Mas vamos fazer algo simples e alterar apenas o esquema, o que permite que você faça muitas coisas comuns.
Então, digamos que eu queira apenas eliminar o campo de descrição e alterar o ano para um número inteiro.
Altere a data para um número inteiro.
Você sabe, o que quiser fazer.
Estou apenas brincando aqui e isso faria o que você espera.
Portanto, clique nela.
E você também pode examinar o esquema de saída para ter certeza de que ele fez o que você disse.
A descrição desapareceu: ano e dia agora são um número inteiro.
E vamos também aplicar um filtro a isso.
Então, vamos fazer um filtro de transformação.
E poderíamos dizer, por exemplo, para adicionar uma condição.
Digamos que queiramos filtrar tudo o que tiver um ano inferior a 2001.
É simples assim.
Tudo bem.
E clique nela.
E você pode ver que o esquema de saída é o mesmo.
Acabamos de filtrar alguns dados e agora podemos colocá-los em algum lugar.
Então, vamos clicar em mais novamente e adicionar um alvo.
E vamos despejar isso no S3 também.
Novamente, você pode ver que há muitos outros lugares para os quais você pode enviar isso, incluindo snowflake, BigQuery,
Azure.
Eles não se importam.
É incrível.
Mas vamos escolher outro balde S3.
E então eu poderia especificar em qual balde eu quero colocar isso, certo?
E, a propósito, não precisa ser linear assim.
Portanto, esse é, na verdade, um gráfico acíclico direcionado.
Assim, você pode ter coisas acontecendo paralelamente umas às outras.
Se eu quisesse, poderia clicar novamente aqui em cima e fazer esse filtro em paralelo, em vez de depois desse nó de transformação.
Portanto, você pode ter essas estruturas mais complicadas em que o processamento está ocorrendo em paralelo para torná-lo ainda
mais eficiente.
Se isso fizer sentido para o que você está fazendo.
Não precisa ser linear assim.
Tudo bem.
Esse é o Glue Studio, apenas para mostrar a você o que ele é e o que pode fazer.
Vamos voltar para a página anterior.
E, a partir daí, você pode monitorar os trabalhos existentes e ver o que eles estão fazendo.
Da última vez, você os trocou e tudo o mais.
E eles também têm alguns exemplos que você pode examinar.
Então, esse é o Glue Studio.
Sabe, acho que, atualmente, as pessoas estão sendo mais incentivadas a usar os dados do Wrangler.
Mas ele ainda está lá para você.
Também conhecido como ETL visual.
