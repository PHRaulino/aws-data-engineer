no exame como Amazon Datazone.
Então, do que se trata?
Vamos, uh, vamos resolver isso.
Basicamente, é um serviço de gerenciamento de dados e sua ideia é facilitar a catalogação, a descoberta, o compartilhamento
e a administração de dados entre vários projetos e vários grupos de usuários.
Portanto, é mais um tipo de ferramenta de nível empresarial para gerenciar dados.
E quem tem acesso a ele em um nível superior.
Ele funciona com os serviços da AWS, é claro, mas você também pode integrá-lo a dados locais ou
de terceiros se realmente se esforçar.
E seus usuários são mais amplos, portanto, não é necessário usá-lo por meio de uma API ou mesmo
do console do AWS.
Ele tem um aplicativo da Web independente chamado Data Portal, que pode ser usado por engenheiros, cientistas
de dados, gerentes de produtos, analistas ou usuários comerciais.
Assim, você pode decidir que tipo de permissões diferentes pessoas têm quando se trata de seus dados.
Ele promete acesso fácil e seguro aos seus dados, com governança e transparência incorporadas.
Portanto, trata-se de um produto muito bom.
E, a propósito, ele está se tornando um com o SageMaker ultimamente.
Portanto, parece que eles estão migrando isso para o SageMaker Unified Studio, que é uma coisa nova.
E, com o tempo, não me surpreenderia se o Datazone fosse um produto autônomo e desaparecesse e se tornasse
parte do SageMaker.
Mas até o momento desta gravação, em 2025, isso ainda não aconteceu.
Então, para que você usa o Datazone?
Do que se trata?
Portanto, ele serve para catalogar e descobrir dados e tem gerenciamento automático de metadados.
E ele ainda tem alguns recursos legais de IA generativa que podem tentar descobrir o que seus dados significam e escrever
em inglês simples sobre eles para que as pessoas possam realmente descobrir seus dados e do que se tratam.
Usando o inglês simples, não é necessário ser um engenheiro de dados para entender isso.
Ele também fornece acesso a dados de governança e governança.
Ele oferece controle de acesso refinado, de modo que você pode ter muito controle sobre quem pode ver o quê.
E você também pode configurar fluxos de trabalho de governança para descobrir como tudo isso funciona.
Ele foi desenvolvido para a colaboração entre equipes.
Portanto, como você verá em nossa demonstração, ele tem esse conceito de projetos.
E uma equipe pode estar associada a um projeto e ao tipo de acesso que ela tem, aos recursos que possui
e às ferramentas analíticas às quais pode ter acesso dentro desse projeto.
Você também pode usar o Datazone para automatizar fluxos de trabalho e compartilhar dados entre produtores e consumidores.
Portanto, em nossa demonstração, veremos um projeto que produz dados e outro que os consome.
Algumas palavras-chave da Datazone.
No nível mais alto, temos um domínio, que é a entidade organizacional para agrupar usuários,
dados e projetos.
Portanto, esse é o componente organizacional de mais alto nível da Datazone.
O portal de dados é novamente o aplicativo da Web que é executado sobre o Datazone.
E isso está sendo executado fora do console do AWS.
Portanto, qualquer pessoa pode acessá-lo se tiver permissões.
Ele ainda passa pelo IAM, mas não é o console, é seu próprio aplicativo da Web autônomo.
E eles podem usar isso para catalogar dados, descobrir dados de governança de dados, compartilhar dados e
analisar esses dados por meio do portal de dados.
Ele também tem um catálogo de dados comerciais.
Portanto, ao publicar dados, você pode publicar muitos dados sobre esses dados.
Você conhece a taxonomia dos dados.
Glossário de termos para os quais os dados são usados.
Descrições detalhadas do que é cada campo, coisas desse tipo.
E também tem um conceito de projetos de dados.
Portanto, em um domínio, você terá projetos.
Esses projetos reúnem pessoas, conjuntos de dados e ferramentas analíticas.
E você pode pensar nisso como uma equipe, ou seja, um grupo de pessoas responsáveis pela publicação
de dados, pela análise ou pelo consumo desses dados viveria em um único projeto.
E, em projetos, temos ambientes.
Portanto, os ambientes de dados fornecem a infraestrutura usada pelo projeto.
Portanto, é aí que todos os componentes subjacentes das ferramentas de armazenamento ou de análise são de fato configurados
e subjacentes a tudo isso.
Temos controles de governança e acesso.
Portanto, esses são fluxos de trabalho integrados para solicitar acesso aos dados e aprová-los.
Veremos isso em nossa demonstração.
É muito legal.
E ele gerencia todas as permissões para você por meio da formação de lagos sob o capô e também usando
o redshift.
Então, conceitualmente, é assim que tudo se parece.
Portanto, o Datazone em si é aquela caixa no meio.
E, como dissemos, o portal de dados é um aplicativo da Web que é executado sobre tudo isso.
Ele passa por APIs que você também pode usar, se quiser, que ficam no topo do catálogo
de dados comerciais, além dos projetos e ambientes que concedem permissões a usuários individuais e recursos a usuários
individuais em um projeto.
E, por trás de tudo isso, temos a governança e o controle de acesso.
Podemos produzir dados que alimentam esse sistema, e esses dados podem vir do S3, podem vir
do redshift ou podem vir da cola.
E então podemos ter consumidores do outro lado para que você possa consumir esses dados
no Datazone usando o Athena SageMaker QuickSight ou o Redshift Query Editor.
Outra coisa que vale a pena mencionar são os projetos de datazone.
Portanto, quando estiver criando um ambiente, lembre-se novamente de que um ambiente é o que configura os recursos
para um determinado projeto.
Há projetos disponíveis para facilitar um pouco isso, de modo que você pode selecionar um
projeto de data lake que lhe dê acesso ao Athena glue, ETL e material de formação de lake.
A propósito, você também pode personalizá-los.
Portanto, se você precisar mudar a forma como isso funciona, poderá ajustar esses projetos de acordo com suas necessidades.
Há também um projeto de data warehouse se você quiser usar apenas o redshift.
Há também um blueprint do SageMaker se você pretende usar o Datazone apenas no SageMaker em um determinado
ambiente.
E você também pode criar seus próprios blueprints personalizados que definam suas próprias funções de
IAM e seu próprio conjunto de serviços que serão associados a esse ambiente.
Portanto, novamente, um projeto define um ambiente.
Um ambiente é parte de um projeto, e um projeto é parte de um domínio.
E isso fará muito mais sentido com uma demonstração.
Então, vamos nos aprofundar em uma demonstração prática do uso do Datazone.
