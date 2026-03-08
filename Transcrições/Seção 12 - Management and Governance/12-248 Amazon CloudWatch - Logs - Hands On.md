podemos ver todos os grupos de registros que temos no momento.
Portanto, como você
pode ver, temos oito deles e foram criados
por alguns serviços.
Por exemplo, este foi criado pela Lambda.
Este foi criado por datasync.
Este foi criado pelo glue e este foi criado
por nós quando executamos
um SSM runCommand e queríamos que a saída fosse
preenchida nesse grupo de registros.
Então, se dermos uma olhada neste exemplo, por exemplo,
temos seis fluxos de registro e, portanto,
cada um deles representa uma instância diferente na qual executamos
um comando de execução específico.
Portanto, esse é o mesmo ID de runcommond em todos os seis.
Aqui, temos um ID de instância diferente para cada um
dos seis, portanto, dois e dois e, em seguida,
temos stdout e stderr.
Portanto, se olharmos para o stdout, poderemos
ver todos os registros que foram gerados por esse comando e poderemos
dar uma olhada em todas
as linhas de registro e assim por diante.
Portanto, isso é bastante (indistinto).
A ideia é que, a partir
do registro, por exemplo,
você possa procurar a palavra-chave http e
ele mostrará todas as linhas de registro que contêm
a palavra htp.
Se você procurar apenas a palavra installing (instalando), por exemplo,
ele mostrará talvez apenas duas ou três linhas de registro que contenham
a palavra installing (instalando).
Portanto, isso certamente é (indistinto).
Temos, portanto, stdout e stderr, para que possamos
ver a ideia por trás dos diferentes fluxos de registro.
Agora, podemos criar filtros métricos aqui, e esses filtros
métricos são uma forma
de encontrarmos um padrão de filtro.
Por exemplo, instalar.
Ok, e então precisamos
selecionar, por exemplo, um dado
personalizado, por exemplo, esse fluxo de registro
e, em seguida, testamos um padrão e ele nos dará três
correspondências de cinco nos registros simples.
Agora, se você continuar inserindo o nome desse filtro, como
podemos ver, ele
poderá chamá-lo de DemoFilter
e DemometricFilter.
E este é um novo namespace, ok.
E aqui está a DemoMetric.
Portanto, este é o namespace do filtro DemoMetric,
e este é um DemometricFilter.
E depois, o valor métrico, ok.
Quando há um padrão de filtro ou correspondência,
você pode dizer um, por exemplo, para
adicionar um e contar quantas vezes essas linhas
de instalação foram filmadas.
E o valor padrão e a unidade, se você quiser, depois
clique em next, create e isso
lhe dará uma nova métrica, portanto,
se você entrou na métrica do CloudWatch bem aqui,
vamos limpar esse gráfico
e encontraremos uma nova métrica.
Então, vamos atualizar esta página.
Talvez isso nos ajude.
Então, se formos para todos os novos espaços,
assim que esse filtro métrico aparecer, ele aparecerá bem aqui e
poderemos visualizá-lo.
Mas, atualmente, como não enviamos nenhuma saída de
registro, não a vemos.
Mas a ideia
é que possamos criar um alarme em cima
desse filtro de métrica.
e isso nos permitiria criar um alarme caso,
por exemplo, uma
métrica ultrapassasse um valor específico
e, novamente, essa métrica é calculada com base no filtro
dos fluxos de registro.
Também podemos criar filtros de assinatura.
Portanto, como você pode
ver aqui, podemos criar um filtro para diferentes resultados.
Portanto, Elasticsearch, Kinesis, fluxos de dados, Kinesis Firehose
ou um filtro de assinatura Lambda se você quiser enviar
dados para funções lambda personalizadas.
E podemos criar até dois filtros de assinatura
por grupo de registro de acordo com isso, ok.
Agora, também podemos editar as configurações de retenção.
Portanto, podemos ver que os registros
nunca podem expirar até 120 meses.
Certo, então 10 anos.
E, em seguida, também podemos exportar os dados para o Amazon S3.
Então, você pode clicar em exportar
dados. Você pode escolher um intervalo de dados para
exportar e, em seguida, o prefixo
do fluxo, se quiser obter apenas fluxos de log
específicos, e, em seguida, os buckets do S3 e o prefixo
do bucket, e pronto.
E, finalmente,
aqui você pode criar um grupo
de registro (indistinto) demo-log-group.
Pronto, você pode definir as configurações de retenção.
Chave KMS, se quiser criptografar esse grupo de registros
e, em seguida, clique em criar.
Portanto, a configuração de criptografia apareceria aqui, se
uma ID de chave KMS fosse especificada.
E, por fim, o CloudWatch Logs Insights
permite que você use uma boa
linguagem de consulta para consultar alguns grupos
de registros específicos.
Assim, por exemplo, podemos criar
este e executar a consulta.
E isso não nos fornecerá nenhum dado, pois estamos
procurando dados da última hora.
Mas se analisarmos os dados dos últimos 60 dias e executarmos essa
consulta, talvez encontremos algo.
Como você pode ver, encontramos
18 registros dessa consulta.
Portanto, isso nos dá uma boa linguagem de consulta
para começar a obter alguns insights sobre os nossos registros.
E, além disso, você
pode exportar os resultados, se desejar.
E no lado direito, você pode ver
que pode salvar suas consultas. Está bem?
Portanto, você pode consultá-los e salvá-los aqui.
Por exemplo, visualizar
as estatísticas de latência para um intervalo de cinco
minutos no Lambda
ou obter as 10 principais transferências
por endereços IP de origem
e destino para logs de fluxo VPC.
Isso lhe dá, por exemplo,
se você clicar neles, alguns insights
interessantes sobre como a linguagem de consulta funciona para os
insights dos registros do CloudWatch.
Portanto, esses são os registros do CloudWatch.
Espero que tenham gostado
e nos veremos na próxima palestra.
