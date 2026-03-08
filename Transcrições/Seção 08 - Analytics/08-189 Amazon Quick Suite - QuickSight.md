QuickSight, que é a ferramenta de visualização da AWS para big data.
O que é o QuickSight?
Bem, a definição oficial da Amazon é que se trata
de um serviço de análise
de negócios rápido, fácil e baseado na nuvem.
Vamos detalhar isso.
Então, sim, é basicamente um serviço para
visualizar seus dados, e a parte
rápida e fácil da nuvem significa que ele é dimensionável
e não se destina apenas a desenvolvedores.
Na verdade, trata-se mais de um aplicativo da
Web em que qualquer pessoa em sua organização
pode usá-lo para ver painéis ou criar seus próprios painéis, criar
seus próprios gráficos e diagramas,
o que for necessário para interpretar seus dados e procurar tendências e outras
coisas do ponto de vista comercial.
Portanto, ele foi criado para pessoas que entendem de dados,
mas não necessariamente são desenvolvedores.
Ele permite que todos os funcionários de uma organização,
e não apenas os desenvolvedores,
criem visualizações com base em seus dados.
Você também pode criar relatórios paginados para a gerência.
Na verdade, esse é um novo recurso do QuickSight,
acredite ou não.
Você acha que ele estará
lá, mas eles descobriram isso recentemente.
Você pode usá-lo para realizar análises ad-hoc.
Portanto, ele pode ser colocado sobre seu data
lake, seu data warehouse, quaisquer que sejam
seus dados - falaremos sobre essas fontes em breve - e obter
uma visualização em tempo real desses dados à medida que eles mudam.
Portanto, se você quiser se aprofundar nos dados mais recentes
e entender como eles estão se comportando, quais são as tendências
e o que isso significa para a empresa,
poderá configurar rapidamente novas visualizações, dar uma olhada
nos dados, interpretá-los,
tentar entendê-los e aplicá-los à sua empresa.
Você também pode receber alertas sobre anomalias detectadas.
Portanto, há um recurso
em que ele pode monitorar automaticamente seus
dados e dizer: "Ei, há algo fora do comum aqui.
Talvez você deva fazer algo a respeito, pessoa. Você também pode, de forma mais geral,
usá-lo para obter insights
comerciais de seus dados muito
rapidamente.
Esse é o objetivo do QuickSight.
Essa é a parte rápida, eu acho.
Portanto, essa deve ser uma maneira relativamente fácil
de visualizar seus dados.
Você não precisa necessariamente saber SQL, embora isso
ajude, mas há alguns recursos que tentarão criar automaticamente
uma visualização adequada apenas inspecionando os dados
e tentando descobrir isso por conta
própria.
Portanto, conhecer o SQL ajuda.
Mas não é necessário.
E foi desenvolvido para qualquer dispositivo.
Portanto, mesmo que você seja um CEO que
queira ver os painéis mais recentes
da empresa em seu celular, o QuickSight
pode ser o front-end para isso.
E é totalmente sem servidor, é claro.
Não queremos que seu CEO tenha que se preocupar
com quantos servidores
estão sob o capô, alimentando o QuickSight.
Tudo é dimensionado para cima e para baixo automaticamente.
Há muitas fontes de dados que o QuickSight pode utilizar.
Então, onde estão os dados que você deseja visualizar?
Isso é algo com que você pode ter que se preocupar
como desenvolvedor.
A escolha óbvia é o Redshift.
É claro que você pode ter um data
warehouse gigantesco e só quer fazer alguns
gráficos e relatórios sobre
esse data warehouse.
Você pode se sentar em cima de qualquer banco
de dados Aurora ou RDS.
Portanto, se você estiver executando
alguma instância do MySQL
ou algum tipo de banco de dados SQL, poderá colocar
o QuickSight sobre ele também.
Athena, também uma escolha popular.
Portanto, se você tiver um
grande lago de dados no S3 ou algo assim,
poderá ter o Athena sobre ele e, em seguida,
visualizar por meio do Athena os dados
em seu lago de dados.
Portanto, esse é um recurso interessante, certo?
Sem sequer ter um "banco de dados real".
Você pode simplesmente
ter uma coleção de dados não estruturados no S3 em
algum lugar e não apenas consultá-los por
meio do Athena, mas também visualizar esses dados usando o QuickSight.
Ele também pode se comunicar com o OpenSearch.
Portanto, o caso de uso é um pouco mais obscuro, mas
você poderia colocar o QuickSight
sobre um banco de dados OpenSearch, se quisesse.
Muitas vezes, as pessoas colocam seus dados de servidor, seus
dados de registro de servidor no OpenSearch.
Portanto, se você quiser visualizar
isso e observar coisas como latências
de servidor ou códigos de resposta ao longo do tempo, também
poderá fazer isso com o QuickSight.
Ele também se integra à análise de IoT, à Internet
das coisas, embora a AWS não esteja enfatizando tanto isso atualmente.
E se você tiver um banco de dados hospedado no EC2,
talvez tenha colocado sua própria instância
do MySQL em uma instância do EC2 em algum lugar, o QuickSight
também poderá se comunicar com ela.
Além disso, basta desenhar arquivos.
Você pode ter arquivos CSV ou TSV, arquivos de valores separados
por tabulação ou por vírgula, ou até mesmo
arquivos do Excel, ou até mesmo
formatos de log comuns armazenados em algum lugar no S3 ou no
local, em algum lugar que o QuickSight
possa acessar de alguma forma, e ele também
pode visualizar isso diretamente.
Antes de analisar ou visualizar, você
pode até mesmo preparar esses dados, se quiser,
de forma limitada no QuickSight.
Portanto, se você precisar
fazer coisas como alterar os nomes das colunas em seu arquivo,
poderá fazer isso.
Altere os nomes dos campos, adicione campos calculados, você pode
usar consultas SQL.
Você pode alterar os tipos
de dados, se precisar fazer um pouco de ajuste nos dados
antes de visualizá-los, o que também
pode ser feito no QuickSight.
Uma parte importante do QuickSight é o SPICE, e
esse é o truque que ele usa
para acelerar suas consultas.
SPICE significa super-rápido, paralelo,
no mecanismo de cálculo da memória.
Portanto, é uma maneira de copiar seus
dados do Athena em um formato mais otimizado
que leva a consultas mais rápidas do QuickSight.
Portanto, a ideia é usar armazenamento em colunas,
acesso na memória, geração de código de máquina e acelerar
suas consultas interativas em conjuntos
de dados muito grandes.
É claro que isso requer espaço, capacidade de armazenamento.
Basicamente, ele precisa copiar
muitos de seus dados do Athena para essa
representação mais compacta e otimizada que o SPICE usa.
Cada usuário recebe 10 gigabytes de SPICE por padrão.
Ele promete ser altamente disponível
e durável, assim como o S3 seria, e pode ser dimensionado
para centenas de milhares de usuários.
Portanto, eles o tornaram disponível, durável e dimensionável.
Portanto, a ideia do SPICE
é apenas acelerar suas consultas,
mas é uma camada extra.
Portanto, às vezes é preciso pensar nisso.
Portanto, embora ele possa acelerar consultas muito grandes que normalmente não seriam
atendidas se você estivesse usando
o modo de consulta direta, o modo de consulta
direta é uma outra palavra para dizer
que o Athena é acionado diretamente.
Você pode chegar a uma situação em que
as consultas são grandes demais até mesmo para o SPICE.
Portanto, uma situação que você pode encontrar
é que, se levar mais de 30 minutos para
importar os dados do Athena para o SPICE, o tempo de espera
ainda vai acabar.
Portanto, embora o SPICE tenha sido projetado para acelerar
consultas grandes com o QuickSight, ainda há um limite máximo que
você pode atingir.
Portanto, é preciso estar atento a isso.
Mas lembre-se de que o SPICE é o
mecanismo de cálculo super-rápido,
paralelo e na memória que
existe para oferecer uma representação mais otimizada
dos seus dados e acelerar suas consultas
interativas por meio do QuickSight, especialmente em grandes
conjuntos de dados.
Mas, você sabe, é possível ficar tão grande que
nem mesmo o SPICE consegue lidar com isso.
Aqui estão alguns dos casos de uso
que a Amazon recomenda para o QuickSight.
Uma delas é a exploração interativa ad-hoc
e a visualização de dados.
Portanto, você deve se lembrar
de que isso é, na verdade, explicitamente um antipadrão
em outros serviços.
No entanto, o QuickSight foi projetado
desde o início para exploração e visualização ad-hoc de seus dados.
Você também pode criar painéis com o QuickSight.
Portanto, você pode criar esses painéis agradáveis
para visualizar os dados periodicamente e
garantir que seus executivos possam vê-los
e saber como a empresa está se saindo.
Ele também é útil para analisar
ou visualizar dados de várias fontes, incluindo
logs do S3, quaisquer bancos de dados que você possa ter no local, outros
serviços da AWS que listamos anteriormente: RDS, Redshift,
Athena e S3.
Você também pode integrar
o QuickSight a aplicativos como o Salesforce, o que pode ser útil.
Qualquer aplicativo de software como
serviço provavelmente pode se integrar
ao QuickSight e a qualquer fonte de dados JDBC ou ODBC.
Portanto, praticamente qualquer fonte de dados que você possa imaginar, o QuickSight
pode importá-la e permitir
que você a visualize muito rapidamente
e em grande escala.
No entanto, há algumas coisas para as quais o QuickSight não foi feito
e, embora tenha recursos limitados de ETL, se você quiser
fazer transformações de ETL
mais poderosas ou em maior escala em seus dados, o QuickSight realmente
não é a ferramenta para isso.
Em vez disso, você deve usar o Glue ETL ou talvez o Apache Spark.
Mas, novamente, o QuickSight tem
algumas transformações limitadas que podem
ser feitas apenas para melhorar um pouco a aparência dos dados.
Do ponto de vista da segurança, ele oferece
autenticação multifator nas contas que
acessam o QuickSight.
Lembre-se de que esta é mais uma ferramenta para
o usuário final, portanto, você
não usará recursos de segurança de nível inferior com ela.
No entanto, ele tem conectividade VPC.
Portanto, você pode adicionar o intervalo de endereços IP do QuickSights
aos grupos de segurança do seu banco de dados.
Você terá de se preocupar com
a forma como o QuickSight se comunicará com seus bancos
de dados e passará pela segurança que você tem sobre eles.
Ele também oferece segurança em nível de linha,
ou RLS, que permite que os proprietários de conjuntos de dados do QuickSight
controlem o acesso aos dados na granularidade da linha com base nas
permissões associadas ao usuário
que interage com os dados.
E com o RLS ou segurança no nível da linha, os usuários do QuickSight
só precisam gerenciar um único conjunto de dados e aplicar a ele as regras
apropriadas de conjunto de dados no nível da linha.
No final de 2020, eles também adicionaram segurança em nível de coluna ou CLS.
Isso está presente
apenas na Enterprise Edition do QuickSight,
mas permite que você gerencie a segurança no nível da coluna,
bem como no nível da função.
Você também tem acesso ao VPC privado disponível,
que é possível
por meio da Elastic Network Interface ou ENI para criar
uma comunicação privada segura com fontes
de dados e um VPC que também usa o AWS Direct Connect para criar um link seguro e privado
com seus recursos no local.
Portanto, se você quiser usar
o QuickSight sobre bancos de dados ou arquivos locais, poderá
usar o Direct Connect para fazer isso.
Um pouco mais sobre segurança e QuickSight.
Então, como você gerencia o acesso aos recursos?
Bem, é bem simples, na verdade.
No console do QuickSight, há um
menu gerenciado do QuickSight
e, a partir dele, você pode ir para segurança e permissões
e, a partir daí, garantir que o próprio QuickSight esteja
autorizado a usar o Athena S3 e, especificamente,
seus buckets S3.
Portanto, antes de chegar ao nível do usuário,
é preciso garantir que o próprio QuickSight esteja
autorizado a acessar os dados que você deseja,
estejam eles no Athena ou no S3.
E, novamente, isso pode ser gerenciado
diretamente no console do QuickSight.
Agora, se for necessário
restringir o acesso de usuários específicos, é
possível criar políticas de IAM para restringir os dados no S3 que um determinado usuário
do QuickSight pode acessar.
Portanto, lembre-se de que é necessário garantir que o
próprio QuickSight esteja autorizado a acessar
seus dados, e você também pode precisar controlar quais usuários podem
acessar quais dados por meio de políticas de IAM.
Portanto, o próprio QuickSight
pode ser gerenciado por meio do console do QuickSight,
mas se você precisar de permissões mais granulares
no nível do usuário, o IAM poderá ser usado para isso.
Portanto, há também a questão específica do QuickSight
e do Redshift juntos do ponto de vista da segurança.
E, de modo geral, o QuickSight tenta lidar
com todas essas coisas nos bastidores
para você, porque
ele é mais voltado para usuários finais
e não para especialistas em
AWS, mas essa é uma área que pode atrapalhá-lo.
Portanto, por padrão, o QuickSight
só pode acessar dados armazenados
na mesma região em que você
está executando o QuickSight.
Portanto, você pode ter uma
situação em que um cluster Redshift
existente esteja em execução em alguma região, como o Japão ou algo
assim, mas o QuickSight tenha sido iniciado na Virgínia
e, nesse caso, você receberá erros
porque essas duas regiões não podem se comunicar.
Você pode pensar que poderia simplesmente criar uma VPC
e configurá-la para funcionar em todas as regiões,
mas isso, na verdade, não funciona com o QuickSight.
Se você tiver essa situação,
a maneira de corrigi-la é criar um novo grupo de segurança
com uma regra de entrada que autorize o acesso a partir do intervalo de IP
dos servidores do QuickSight nessa região.
Então, estou destacando isso por um motivo, pessoal.
Felizmente, esses intervalos estão
documentados, você
precisa pesquisá-los, mas essa é a etapa que
você deve seguir se precisar ter acesso ao
QuickSight, um cluster do Redshift que está em uma região diferente, configurar
um novo grupo de segurança com uma regra
de entrada com o intervalo de IP de onde estão os servidores
do QuickSight.
E você precisa pesquisar quais são esses intervalos de IP.
Agora, se você tiver a edição Enterprise do QuickSight,
há maneiras de lidar com o problema de cruzamento de regiões para
obter dados do QuickSight em uma região para
o Redshift ou até mesmo para o RDS, que pode estar em uma
região diferente.
E essas mesmas técnicas, em alguns casos, também
funcionam para o acesso entre contas.
Portanto, novamente, se você tiver
a Enterprise Edition,
poderá criar uma sub-rede privada em uma VPC e
usar a Elastic Network Interface para
colocar o QuickSight nessa sub-rede dentro da VPC.
Agora, acessar o QuickSight de dentro de uma sub-rede
privada é a parte que requer o Enterprise Edition,
mas, depois de fazer isso, todas
as várias técnicas de conexão de sub-redes entre
regiões ou entre contas ficam disponíveis para você.
Então, vamos nos aprofundar no que acontece a partir daí.
Portanto, essa é a primeira etapa, não importa como você esteja fazendo isso.
Você precisa colocar o QuickSight em uma sub-rede privada em uma VPC
usando a Elastic Network Interface ou ENI.
Uma maneira de fazer o acesso entre
regiões é também colocar o RDS, o Redshift ou
qualquer outro tipo de dados em outra sub-rede privada e, em seguida,
conectá-lo à sub-rede privada que
tem o Quick Knight usando uma conexão de peering, certo?
Basicamente, você coloca o QuickSight
em uma sub-rede privada.
Você tem o RDS ou o Redshift dentro de outra sub-rede privada que
pode estar em uma conta diferente,
pode estar em uma região diferente, mas
ainda é possível uni-los usando
uma conexão de peering para obter acesso entre regiões.
Esse é o tipo de coisa sobre
a qual o exame adora questioná-lo,
portanto, tente internalizar isso.
Isso não é útil apenas para acesso entre regiões, mas também
pode ser usado, em alguns casos,
para acesso entre contas.
E se seu objetivo for o acesso entre contas,
há algumas outras maneiras de fazer isso também.
Basicamente, se você substituir a conexão de peering
pelo AWS Transit Gateway, essa será outra maneira
de conectar duas sub-redes diferentes.
No entanto, o Transit Gateway em si é limitado
a estar dentro da mesma organização e região entre as coisas que você
está tentando conectar.
No entanto, é possível combinar Gateways de trânsito entre si.
Portanto, essa pode ser uma maneira
prática de conectar as coisas se você quiser obter acesso entre contas quando essas
contas estiverem na mesma organização na mesma região.
Caso contrário, é melhor usar apenas o peering, certo?
Outra abordagem é usar o AWS Private Link.
E, basicamente, isso substituiria o Private
Link pelo AWS Transit Gateway
no diagrama superior, a mesma ideia.
Outra técnica é usar o compartilhamento de VPC.
E você pode ver isso
no diagrama inferior aqui à direita.
Isso significa usar duas sub-redes
privadas, uma para o QuickSight e outra para a fonte
de dados, e depois usar o Compartilhamento de VPC para uni-las.
Novamente, uma maneira de fornecer acesso
a duas contas diferentes.
Você pode ver que o diagrama aqui
fala sobre a conta A e a conta B.
Portanto, esse é realmente o objetivo dessas abordagens.
Portanto, lembre-se de que todas essas são maneiras de lidar com
o acesso entre regiões e entre contas.
Se seu objetivo for o acesso entre regiões, o peering é provavelmente
o caminho a seguir.
Mas se você quiser acesso entre
contas, o Transit Gateway, o Private Link ou o VPC Sharing
podem ser viáveis, dependendo de seus requisitos.
Fale um pouco sobre o QuickSight User Management.
Como você realmente gerencia quem tem acesso a ele?
Novamente, você sabe, a AWS tenta tornar o QuickSight
amigável para o usuário final.
Portanto, você pode definir usuários no IAM e fazer isso dessa forma.
Isso lhe dá um controle mais rigoroso
sobre o que os usuários individuais
podem ou não acessar em termos de quais
dados, quais buckets S3 subjacentes, quais bancos de dados Redshift, etc.
Ou você pode configurá-lo para
que as pessoas se inscrevam por e-mail e sejam
aprovadas dessa forma.
Portanto, essa é uma maneira mais fácil de configurar as coisas, se
você se sentir confortável com isso.
Também é importante entender que
a integração com o Active Directory também está disponível
no QuickSight.
Existe um recurso chamado Active Directory Connector.
Isso só é oferecido no QuickSight Enterprise Edition.
E, novamente, com o intuito
de facilitar ao máximo as coisas, com o Active
Directory Connector, todas
as chaves são gerenciadas pelo AWS para o QuickSight.
Não é possível usar chaves fornecidas pelo cliente com
o Active Directory com o QuickSight.
Além disso, lembre-se de que o suporte ao Active
Directory está disponível apenas na Enterprise Edition.
Agora, o que você pode fazer é configurar diferentes grupos de usuários
que correspondam a grupos de usuários do Active Directory e ajustar
o acesso de segurança deles usando o IAM, se necessário.
Portanto, você ainda pode configurar grupos de
usuários por meio do Active Directory
e ajustar o que eles podem ou não acessar usando o IAM.
Portanto, a conclusão aqui é que o
ponto de partida básico da segurança no QuickSight é o IAM.
Você pode usar isso para definir o que os usuários podem ou não fazer.
Registro de e-mail como uma opção.
E se você estiver usando o Enterprise Edition,
poderá usar o Active Directory Connector, mas lembre-se
de que as chaves são todas gerenciadas pelo AWS.
Não é possível usar chaves fornecidas pelo
cliente, e isso só é suportado na Enterprise Edition.
