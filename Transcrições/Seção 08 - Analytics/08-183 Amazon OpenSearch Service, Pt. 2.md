Então,
e o que ele tem em comum com o Amazon OpenSearch.
Vamos nos aprofundar no serviço OpenSearch propriamente dito
e falar sobre como ele realmente difere do Elasticsearch.
Portanto, há algumas variantes diferentes do OpenSearch.
Há a versão gerenciada,
sobre a qual falaremos nos próximos slides.
Há também uma versão sem servidor,
uma opção totalmente sem servidor
agora, e falaremos sobre isso em alguns minutos.
Mas, por enquanto, vamos falar
sobre a solução totalmente gerenciada.
Há dois universos paralelos diferentes do OpenSearch,
se você preferir.
Uma que seja uma solução gerenciada, como o RDS ou
o EMR como gerenciado.
E há uma solução totalmente sem servidor,
na qual você não pensa nos servidores subjacentes.
No entanto, na solução gerenciada,
é possível aumentar e diminuir a escala sem tempo de
inatividade, de modo que você pode alterar o
número de hosts que tem no cluster do OpenSearch,
mas ainda precisa pensar em quantos nós existem.
Isso não é feito automaticamente para você na solução gerenciada.
É pagar pelo que você usa.
Portanto, você só paga com base nas horas da instância, na quantidade
de armazenamento que está usando e na
quantidade de transferência de dados.
Agora, observe que você será cobrado, mesmo que
esteja sentado sem fazer nada.
Portanto, se você tiver um cluster do
OpenSearch que esteja ocioso, sem uso, ainda estará
pagando por essas horas de instância.
Portanto, lembre-se de desligá-lo se não o estiver usando,
caso contrário, terá que pagar uma conta bem alta, certo?
Ele oferece um alto nível de isolamento de rede.
Portanto, com o Amazon VPC, você pode garantir a segurança
dos dados criptografando os dados em repouso e em trânsito usando
chaves, e pode gerenciar a autenticação
e o controle de acesso com as políticas do
Amazon Cognito ou do AWS IAM.
Vários pontos de integração aqui.
Eles podem se conectar aos buckets do S3 por meio do Lambda Kinesis.
Ele pode se integrar aos fluxos de dados do Kinesis.
Ele pode se integrar aos fluxos do DynamoDB.
E, é claro, ele se integra ao CloudWatch
e ao CloudTrail.
Portanto, essas são extensões do Elasticsearch
que obviamente não existem na versão não específica do AWS do Elasticsearch.
Isso é o que eles adicionaram para
integrá-lo ao ecossistema da AWS.
Ele também oferece reconhecimento de zona.
E ao alocar zonas em várias zonas de disponibilidade na mesma
região, você pode aumentar sua alta disponibilidade usando o reconhecimento
de zona.
No entanto, isso pode causar latência.
Há algumas coisas que você deve perguntar
que são um pouco específicas da implementação da Amazon aqui.
Uma delas é: quantos nós mestres dedicados você deseja?
E você precisa escolher quantos
deles e que tipo de instância deseja usar.
Agora, os nós mestres são usados apenas para o gerenciamento
do domínio OpenSearch que você está criando e
não retêm nem processam nenhum dado.
Portanto, em geral, você não precisa de muitos deles,
a menos que seu cluster seja realmente enorme.
O que é um domínio?
Bem, novamente, esse é um tipo de coisa específica da Amazon.
E um domínio de serviço do Amazon OpenSearch é uma coleção
de todos os recursos necessários para executar
o cluster do OpenSearch.
Portanto, ele contém toda a configuração
do cluster como um todo.
Então, basicamente, um cluster,
na linguagem do Amazon OpenSearch, é um domínio.
Ele também permite que você habilite instantâneos automáticos
para o S3 para fins de backup de dados.
Portanto, se você desligar inadvertidamente
o cluster, não perderá esses dados.
E, como dissemos, o reconhecimento de zona também é uma opção se
você quiser aumentar a disponibilidade
ao preço de uma latência mais alta.
A segurança é sempre um ponto importante no exame,
portanto, vamos falar sobre como os sistemas de segurança da Amazon
se integram ao Amazon OpenSearch.
Vamos nos aprofundar
nesse assunto quando fizermos o exercício um pouco mais.
Ele permite políticas baseadas em recursos,
portanto, você pode anexá-las ao domínio
de serviço que determina quais ações o princípio
pode executar na API do OpenSearch.
Você também pode ter políticas baseadas em identidade usando políticas
de IAM ou políticas baseadas em IP para vincular ações específicas
a intervalos de IP específicos.
Você também pode assinar suas solicitações
no Amazon OpenSearch.
De fato, é necessário.
Todas as solicitações ao Amazon OpenSearch devem ser assinadas.
E quando você enviar solicitações dos SDKs do AWS para o OpenSearch,
isso lhe dará os meios necessários para realmente assinar
digitalmente todas as solicitações que forem enviadas.
Caso contrário, todo esse tráfego
seria apenas um dado JSON não criptografado.
E, obviamente, essa não é uma abordagem
muito segura quando se está enviando coisas em voo pela Internet.
Agora, para aumentar a segurança,
você também pode colocar seu cluster em
uma VPC em vez de torná-lo público,
o que dará mais segurança ao
seu cluster do OpenSearch em
vez de deixá-lo acessível
ao mundo externo.
É claro que isso dificulta a conexão com
o cluster e o uso de ferramentas como o painel,
mas falaremos sobre isso no próximo slide.
Agora, lembre-se de que não é possível configurar
o cluster primeiro em uma VPC e depois movê-lo para fora da VPC ou vice-versa.
É preciso decidir antecipadamente se o cluster
ficará em uma VPC ou se será acessível ao público.
Você não pode mudar isso depois.
E, por fim, ele se integra ao Cognito.
E, principalmente, isso é útil no contexto
de conversas com dashboards, anteriormente conhecidos como Kibana.
Portanto, se você estiver hospedando seu
cluster do OpenSearch em
uma VPC, como vai acessar seus painéis
pela Internet, por meio de um navegador da Web?
Você acessa os painéis por meio de uma interface da
Web, portanto, ele precisa ser capaz de entrar em seu
cluster e abrir uma conexão HTTP
para realmente visualizar e interagir com os painéis.
Portanto, a maneira mais simples de lidar com isso é usando o Cognito.
O AWS oferece uma integração com o serviço Cognito, que permite que os usuários
finais façam login no painel por meio de um provedor de entidade
corporativa, como o Microsoft Active
Directory, usando SAML 2. 0, e também por meio de provedores
de identidade social, como o Google,
o Facebook ou a Amazon.
Portanto, você pode configurar as coisas
de modo que o Cognito permita que as pessoas façam login
usando a conta do Facebook ou qualquer outra conta, e isso concederá
a elas acesso para realmente
entrar no seu painel, mesmo que ele esteja
oculto atrás de um VPC.
Você também pode configurar experiências
de logon seguras, dimensionáveis e simplificadas
usando os pools de usuários do Amazon Cognito.
Isso facilita um pouco o gerenciamento
dessas coisas, mas ainda é difícil entrar em uma VPC pelo lado de fora.
Agora, há maneiras de contornar isso.
Uma delas é usar um servidor proxy reverso, e
é isso que estamos mostrando aqui
neste diagrama à direita.
Portanto, o Nginx é um exemplo de servidor proxy reverso que
você poderia executar em algum host EC2 em algum
lugar e que, em seguida,
daria a volta e encaminharia a solicitação para o
domínio OpenSearch dentro da VPC.
Você também pode abrir um túnel SSH na porta 5601, que
é a porta em que o painel escuta.
E outras opções para entrar no painel
a partir da VPC incluem o VPC Direct Connect ou apenas o uso
de uma VPN para entrar no painel.
Existem alguns antipadrões e maneiras
pelas quais você não deve usar o serviço OpenSearch da Amazon.
Essas informações foram extraídas diretamente do AWS Big Data Whitepaper,
que, mais uma vez, recomendo fortemente que você leia.
Um deles é o OLTP.
Embora seja muito rápido, ele
não foi planejado para ser usado como um serviço da Web,
portanto, não tem nenhum suporte transacional como
um banco de dados real teria.
Se você for fazer coisas desse
tipo, o RDS ou um DynamoDB pode ser uma opção melhor.
Consulta de dados ad-hoc.
Bem, não tenho certeza de que
isso seja um antipadrão,
pois é possível fazer isso usando painéis.
Mas a AWS prefere usar o Athena para esse tipo de coisa porque,
bem, é para isso que esse serviço foi realmente criado.
Mas lembre-se,
o Amazon Open é principalmente para pesquisa e análise.
Esse é o principal grupo
em que o Amazon OpenSearch se encaixa.
Portanto, se estiver procurando
uma solução de pesquisa ou análise para um problema,
o Amazon OpenSearch pode ser uma solução em potencial para isso.
