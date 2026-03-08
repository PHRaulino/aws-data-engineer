nos aprofundar no Amazon's Opensearch Service,
que era conhecido anteriormente como Amazon's Elasticsearch Service.
Entraremos na história em breve, mas é uma tecnologia
bastante interessante para fazer
análises e relatórios em grande escala,
em escala de petabytes.
E o interessante é que, embora o Opensearch, antigo Elasticsearch,
tenha começado como um mecanismo de busca, e é basicamente para isso que
ele foi criado originalmente.
Na verdade, não é mais apenas para pesquisa, mas
principalmente para análises e relatórios atualmente.
E, para alguns aplicativos, eles
podem realmente analisar conjuntos de dados maciços
como esses com muito mais rapidez do que algo como o Apache Spark.
Portanto, para os tipos certos de consultas,
o Opensearch pode ser uma ótima opção
para obter respostas muito rapidamente
em um conjunto de dados massivo que pode
abranger petabytes em um cluster inteiro.
Então, vamos nos aprofundar no que se trata.
Então, o que é o Opensearch?
Bem, vamos entrar no drama aqui.
Portanto, o Opensearch é uma bifurcação do Elasticsearch e do Kibana.
Portanto, há um pouco de drama aqui.
Basicamente, houve uma disputa de licenciamento
entre a Elastic e a Amazon.
Então, originalmente, a Amazon estava
oferecendo o serviço Amazon Elasticsearch,
que era apenas o produto Elasticsearch em seus servidores,
basicamente.
A Elastic não gostou muito
do fato de a empresa ter consumido
sua receita dessa forma, então alterou a licença do Elasticsearch,
o que forçou a Amazon a criar seu próprio ramo,
que ela mesma mantém e chama de Opensearch.
Tudo isso aconteceu em setembro de 2021.
Portanto, até o final de 2021, você provavelmente
continuará a ver esse serviço sendo chamado de Amazon
Elasticsearch Service no exame e
em outros lugares.
Agora, eles estão chamando o Elasticsearch de Opensearch, e o Kibana
era, na verdade, a ferramenta de visualização que fazia parte
do que chamamos de Elastic Stack.
Portanto, o Elasticsearch fazia parte de um ecossistema maior da Elastic que
incluía o Elasticsearch,
uma ferramenta de visualização chamada Kibana e também algumas
ferramentas de ingestão de dados chamadas Beats.
Mas para o Opensearch,
é apenas uma bifurcação do Elasticsearch no Kibana,
que agora está sendo chamado de Opensearch and Dashboards.
Mas a principal conclusão é que o Opensearch
é fundamentalmente um mecanismo de pesquisa.
Assim, você pode enviar solicitações no estilo JSON e dizer: "Vá
indexar este documento".
E outra solicitação JSON para dizer:
vá procurar documentos que contenham
essas palavras-chave ou esses atributos, ou
podemos fazer coisas como correspondência difusa
e coisas do gênero também.
Portanto, em sua essência, o Opensearch é realmente
um mecanismo de pesquisa muito bom, escalável e muito rápido.
Na verdade, ele foi desenvolvido
com base em uma solução de código aberto chamada Lucene.
Portanto, temos uma espécie de camadas em que o Elasticsearch
foi construído sobre o Lucene e, em seguida,
o Opensearch foi ramificado do Elasticsearch.
É muito complicado, mas foi assim que chegamos até aqui.
Mas, fundamentalmente,
o Opensearch é uma versão escalável do Lucene e é distribuído
horizontalmente em vários
nós em um cluster.
No entanto, ele foi ampliado ao longo dos
anos para incluir cada vez mais ferramentas
e se tornar mais uma análise em uma ferramenta de visualização.
Portanto, outra parte do pacote Opensearch é chamada
de dashboards, que é uma ramificação do que eles
chamam de Kibana no Elasticsearch.
Já está confuso, certo?
Basicamente, é uma ferramenta de visualização
para consulta, análise e visualização de dados armazenados
no Opensearch.
Portanto, você não precisa se limitar
a armazenar informações de documentos no Opensearch.
Quer dizer, você poderia usá-lo para criar
um mecanismo de busca para a Wikipedia ou algo assim,
mas também pode usá-lo para armazenar dados semiestruturados, como dados
provenientes de registros de servidores ou algo assim.
E, se estiver fazendo isso, poderá usar os painéis
para visualizar esse tipo de dados
e criar seu próprio painel do Google Analytics, se preferir,
do zero.
Ele também serve como um pipeline de dados.
Assim, eles percebem que há
uma necessidade de realmente alimentar
dados em escala no Elasticsearch ou Opensearch agora.
E, da mesma forma, você pode usar tecnologias
como Kinesis e Kafka para fazer isso em outros sistemas.
No Opensearch, você provavelmente usaria o Kinesis
para lidar com a ingestão de
dados dos seus servidores no Opensearch.
Agora, no mundo do Elasticsearch, havia
tecnologias chamadas Beats e LogStash que
também faziam isso para você.
Certamente, no exame, você pode esperar
que eles falem sobre a integração do Kinesis com
o Opensearch, em vez da integração do Beats e do LogStash, porque
eles estão tentando se afastar de todo esse mundo.
Mas é disso que se trata o Opensearch.
Basicamente, é o Lucene escalonado infinitamente à medida que
você adiciona mais servidores ao seu cluster.
Por isso, prometi a você uma análise mais detalhada dos dashboards
anteriormente do Kibana.
Aqui está um exemplo de um painel
para que você tenha uma ideia
do que ele é capaz.
E, como dissemos, você pode importar facilmente
dados de registro usando o Kinesis para um cluster do Opensearch e,
em seguida, usar um painel para visualizar esses dados.
Você também pode usar
os painéis como uma espécie de interface de usuário ou front-end
de fácil utilização para consultar esses dados de forma interativa
e experimentar solicitações específicas em seu conjunto
de dados sem precisar digitar linhas de
comando para usar o cURL em um terminal ou algo parecido.
Portanto, este é o aspecto de um painel.
Novamente, pense nele
como uma espécie de painel do Google
Analytics para seus dados armazenados no Opensearch,
e é uma solução muito escalável para isso.
Portanto, algumas empresas não se sentem à vontade
para expor todos os seus dados ao Google ou seus
dados são muito grandes para o Google Analytics processar.
Portanto, para eles, os painéis e o Opensearch
são realmente uma boa alternativa a ser considerada.
Então, para que o Opensearch é usado?
Bem, como eu disse, não é mais apenas para
pesquisa, embora esse ainda seja um ótimo aplicativo.
Se você precisar criar um mecanismo
de busca para um site ou algo
assim, o Elasticsearch é uma ótima ferramenta
para isso, além de ser muito escalonável, de modo que é totalmente
viável criar algo como uma busca na Wikipédia
usando o Elasticsearch ou o Opensearch.
Ainda estou dizendo essas duas palavras.
Eles são a mesma coisa no momento.
Mas ele também serve para outras
coisas, como a análise de registros de que
falamos, e é muito adequado para isso.
Além disso, o monitoramento de aplicativos com base nos dados de registro recebidos.
É uma maneira muito rápida e fácil de visualizar o que
está acontecendo em tempo
real à medida que os dados chegam do monitoramento dos servidores.
A análise de segurança também é um aplicativo
e a análise de fluxo de cliques.
Na verdade, tudo isso se enquadra
na análise de dados de registro,
embora esse seja o tipo de nicho que o Opensearch
começou a preencher.
Portanto, para dar alguns exemplos específicos,
para a pesquisa de texto completo,
o MirrorWeb usa o Amazon Elasticsearch ou o Opensearch
Service agora para tornar pesquisável o arquivo da Web do governo
e do Parlamento do Reino Unido.
E usando o Amazon Opensearch Service MirrorWeb,
o índice é 1. 4 bilhões de documentos,
bilhões com um B, por apenas US$ 337 e indexou 146 milhões
de documentos por hora, o que foi 14 vezes mais rápido do que
a tecnologia anterior que
eles estavam usando.
Como você deve ter percebido, estou falando de estudos
de caso que a AWS oferece e sobre os quais estou falando
aqui, nos quais eles falam sobre como são incríveis, mas
é realmente impressionante
o desempenho e o baixo custo que isso pode ter.
Portanto, para a análise de logs,
a Adobe também usa o Opensearch Service da Amazon e está visualizando
grandes quantidades de dados de logs para sua plataforma
de desenvolvedores.
E, no pico, eles estão recebendo mais de 200.000
chamadas de API por segundo.
Esse é um tráfego bastante surpreendente,
mesmo para mim.
Mas, usando o Amazon Opensearch, a Adobe
pode ver facilmente os padrões de tráfego e as taxas de erro, além
de identificar e solucionar rapidamente qualquer problema em potencial,
tudo isso com uma sobrecarga operacional reduzida,
pois a Amazon faz a manutenção do servidor para eles.
Para o monitoramento de aplicativos em tempo
real, a Expedia é um exemplo de cliente da Amazon, para o qual eles
estão usando o Opensearch Service da Amazon
para monitoramento de aplicativos e análise de causa raiz e
otimização de preços.
E o Amazon Opensearch está permitindo que a Expedia
monitore grandes volumes de logs do Docker de forma econômica, identifique
e solucione problemas em tempo real e dimensione
facilmente para acomodar fontes de log adicionais e descarregar
a sobrecarga operacional, pois, novamente,
é uma solução gerenciada.
No âmbito da análise de segurança, o Amazon
Opensearch permite que você centralize
e analise eventos de toda
a organização em tempo real.
Você pode indexar e analisar seus dados assim
que eles forem recebidos de várias fontes instantaneamente
e localizar e evitar ameaças mais rapidamente.
E, por fim, para a análise de fluxo de cliques,
o exemplo que eles dão é o da Hearst Corporation.
Eles criam uma plataforma de análise de fluxo
de cliques usando o Opensearch Service da Amazon e o Amazon Kinesis Streams
e o Amazon Kinesis Firehose.
Em breve falaremos sobre como tudo isso se encaixa,
mas ele foi desenvolvido para
transmitir e processar 30 terabytes de dados por dia de mais
de 300 sites da Hearst em todo o mundo.
São muitas informações.
E com essa plataforma, a Hearst
pode disponibilizar aos editores, em questão
de minutos, todo o fluxo de dados, desde os cliques
no site até os dados agregados.
Portanto, é em grande escala, quase em tempo real e é barato.
Material incrível. Certo?
Vamos falar sobre os principais conceitos do Opensearch aqui.
Então, basicamente, há três tipos diferentes de entidades sobre
as quais você precisa pensar no contexto do Opensearch.
Um é um documento.
Então, basicamente, o Opensearch é um mecanismo de
armazenamento e recuperação de documentos.
Os documentos são o que você está procurando
e não se limitam apenas a textos.
Você também pode colocar dados JSON estruturados lá.
Agora, cada documento terá um ID de documento exclusivo
que você pode pesquisar.
E atualmente, mas não por muito mais
tempo, também há um tipo associado a ele.
Os tipos são o que define o esquema e o mapeamento
compartilhados por documentos que
representam o mesmo tipo de coisa, como um tipo de entrada
de registro ou um tipo de artigo de enciclopédia.
Basicamente, ele define o esquema que você espera
ver associado a esse tipo de documento.
No entanto, os tipos estão desaparecendo
e estamos mudando para apenas um tipo por índice no momento.
E em versões posteriores do Elasticsearch e,
presumivelmente, em versões posteriores do Opensearch,
eles serão totalmente eliminados.
Na verdade, já na nova interface do usuário do Opensearch,
você verá que o campo de tipo está esmaecido porque
eles não querem mais que você pense
em tipos.
Portanto, hoje falamos mais sobre índices do que sobre tipos.
Um índice possibilitaria a pesquisa em todos os documentos
de uma coleção de tipos.
Um índice também contém um índice invertido
que permite que você pesquise tudo
dentro desse índice de uma só vez.
Portanto, em um Opensearch, temos um tipo por índice.
Portanto, a estrutura esperada é que,
para qualquer tipo de documento, você
tenha um índice separado
específico para esse tipo.
e, por fim, todo o conceito de tipos está desaparecendo
e você pode simplesmente colocar os dados
que quiser em seus dados JSON.
Portanto, mais uma vez, os tipos serão uma coisa do passado em breve.
Portanto, o ideal é pensar apenas em documentos e índices.
Mas se você ainda vir algo
no exame sobre o Elasticsearch 6, os tipos ainda podem
ser uma coisa nesse contexto, mas tenho certeza
de que eles atualizarão o exame em breve,
se ainda não o fizeram, para não falar sobre tipos.
Como tudo isso funciona?
Bem, um índice, que novamente é uma coleção de
documentos relacionados a algo, é dividido em fragmentos.
Então, isso é basicamente uma questão
de escala horizontal direta, certo?
Basicamente, cada documento é associado a um fragmento específico
e cada fragmento pode estar em um nó diferente
dentro de um cluster em algum lugar.
E o interessante é
que cada fragmento no Opensearch
é, na verdade, um índice Lucene autônomo.
Portanto, cada fragmento é uma espécie de mini mecanismo de busca.
É bem legal.
Agora, a redundância funciona da maneira que você esperaria.
Portanto, neste exemplo, temos dois shards primários
e dois shards de réplica para cada primário.
E a maneira como isso funciona é que as solicitações
de gravação seriam roteadas para o fragmento
primário e, em seguida, replicadas para quantas réplicas você especificar.
As solicitações de leitura,
no entanto, podem vir dos shards primários ou de réplicas.
Portanto, cabe ao seu aplicativo fazer um rodízio e tentar distribuir
a carga dessas solicitações de leitura para que você
não coloque toda essa carga no fragmento
principal para leitura.
Você também pode usar essas notas de réplica
para expandir seu rendimento de leitura.
