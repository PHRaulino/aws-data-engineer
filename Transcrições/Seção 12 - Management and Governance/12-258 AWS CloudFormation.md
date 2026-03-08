Bem-vindo a esta
Nesta seção, veremos diferentes
maneiras de implementar suas cargas de trabalho no AWS.
E a primeira tecnologia sobre a qual quero
falar é o CloudFormation.
Portanto, o CloudFormation é uma tecnologia muito importante no AWS
porque é uma forma declarativa
de delinear sua infraestrutura do AWS, para quaisquer recursos,
e a maioria deles é compatível.
Então, para dar um exemplo concreto,
no CloudFormation, você diria: "Quero
um grupo de segurança".
Quero duas instâncias do EC2 que
usarão esse grupo de segurança.
Também quero um bucket S3 e quero um
balanceador de carga na frente de todas essas máquinas.
Em seguida, o CloudFormation cria automaticamente
todos esses itens para você, na ordem certa, com a configuração
exata que você especificar.
Portanto, os benefícios de usar o CloudFormation são vários,
mas o primeiro é
que toda a sua infraestrutura é como código.
Isso significa que
você nunca criará recursos manualmente, como
fizemos neste curso, o que é
excelente para o controle.
Isso significa que sempre que você fizer
alterações no funcionamento da sua nuvem AWS, ela
precisará ser revisada por meio de revisão de código,
o que é uma ótima maneira de operar em uma nuvem.
Além disso, há uma vantagem de custo
porque cada recurso dentro da pilha
receberá uma tag que será semelhante a todos os
outros recursos criados dentro da pilha.
E você também pode estimar facilmente o custo de seus recursos usando
os modelos do CloudFormation.
E, por fim, graças ao CloudFormation, você pode
ter uma estratégia de economia.
Por exemplo, você pode dizer que, em algum ambiente,
é possível automatizar a exclusão de todos os modelos
às 17h, o que excluirá
todos os recursos associados a esse modelo e, em seguida,
recriá-lo às 9h ou às 8h com segurança.
Portanto, você economiza
custos porque não tem recursos
entre as 17h e as 8h.
Com o CloudFormation,
é muito fácil criar e excluir recursos, o que
é um dos maiores princípios da nuvem.
Depois, para a produtividade.
Portanto, como eu disse, você pode
destruir e recriar a infraestrutura em tempo real.
Ele também está gerando diagramas para seus modelos,
como veremos rapidamente.
E há programação declarativa, portanto,
você não precisa descobrir
se precisa criar uma tabela do DynamoDB primeiro, ou uma
instância do EC2, ou todas essas coisas juntas.
O modelo CloudFormation é inteligente o suficiente
para descobrir como fazer as coisas.
Por fim, com o CloudFormation,
não reinventamos a roda.
Isso significa que podemos aproveitar os modelos
existentes na Web,
podemos aproveitar a documentação
e o CloudFormation é compatível com quase todos os recursos da AWS.
Isso significa que tudo o que veremos neste
curso é compatível com o CloudFormation.
E, caso não seja, você
pode usar algo chamado recurso personalizado para
recursos que não são compatíveis.
Portanto, o CloudFormation
é realmente a base da infraestrutura como código no AWS.
Então, como eu disse,
você pode visualizar um modelo do CloudFormation
usando o serviço Infrastructure Composer e
(indistinto) para visualizar
uma pilha do WordPress CloudFormation.
E, como você pode ver, podemos
ver todos os recursos dos nossos modelos
do CloudFormation.
Assim, podemos ver o ALB Listener, o grupo de segurança
do banco de dados, o banco de dados SQL,
diferentes grupos de segurança,
configuração de inicialização,
balanceadores de aplicativos
e assim por diante.
Mas, além disso, podemos
ver as relações entre todos esses componentes e como eles estão
vinculados, o que é muito útil
quando você quer entender
seus diagramas de arquitetura.
Portanto, do ponto de vista do exame,
o CloudFormation será usado quando
tivermos infraestrutura como código, quando
precisarmos repetir uma arquitetura em diferentes
ambientes, diferentes regiões ou até mesmo diferentes
contas da AWS.
Então, para mim, é isso.
Vejo você na próxima palestra
para uma breve prática sobre o CloudFormation.
