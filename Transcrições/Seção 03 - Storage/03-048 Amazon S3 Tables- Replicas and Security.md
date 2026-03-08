Outro recurso das tabelas S3
é a
replicação, que pode ser gerenciada
automaticamente para você.
leitura dos seus buckets de tabela do
S3 para fins de backup, disponibilidade
ou conformidade, basta ativar essa opção.
É muito simples.
Portanto, eles criam réplicas somente
leitura de suas
tabelas S3, e elas podem estar em várias
regiões ou até mesmo em várias contas.
Portanto, se você quiser ter cópias em uma
região diferente para fins de backup ou
até
mesmo em uma conta diferente para
disponibilizar esses
dados para outra organização, poderá usar
a replicação
de tabelas do S3 para conseguir isso.
Alguns casos de uso específicos que podem
ser relevantes aqui.
Portanto, se estiver procurando minimizar
a latência, a replicação de
tabela S3 pode ser uma maneira de fazer
isso.
Se você tiver uma réplica local na região
da qual está acessando os dados, isso
poderá ser usado para melhorar o
desempenho.
Outro caso de uso é a centralização de
suas análises.
Então, digamos que você tenha várias
tabelas S3 em diferentes regiões.
Se quiser replicar todos esses dados em
uma única região, você poderá usá-los para
centralizar sua análise e consultar esses
dados
em uma única região com mais eficiência.
Também pode haver motivos de conformidade
para fazer isso.
Portanto, às vezes há leis sobre onde seus
dados residem se forem confidenciais ou
privados.
E essa é uma maneira de garantir a
conformidade,
dividindo suas tabelas com réplicas em
regiões exclusivas.
Além disso, é útil para ambientes de teste
ou desenvolvimento.
Portanto, se você quiser apenas uma
réplica somente para leitura dos
seus dados, para brincar com eles de
maneira segura e
controlada, poderá usar a replicação de
tabelas para isso também.
Além disso, a classificação inteligente em
camadas
também pode ser aplicada às réplicas, o
que pode minimizar ainda mais seus custos.
Portanto, você pode aplicar o
armazenamento inteligente em camadas a
qualquer réplica e ele prestará atenção à
frequência com que
os dados são acessados e os colocará em
diferentes
níveis de armazenamento para otimizar seus
custos de armazenamento.
Um pouco sobre a segurança da tabela S3.
É sempre importante refletir sobre isso.
Como dissemos, as ferramentas padrão se
aplicam aqui.
É possível usar as políticas baseadas em
identidade do IAM
para controlar o acesso às operações da
tabela S3
no nível do usuário, do grupo ou da
função.
Se desejar, você também pode configurar
políticas
baseadas em recursos vinculadas a buckets
específicos.
E há também a organização com
políticas de controle de serviços, ou
SCPs, por meio do Amazon Organizations.
Além disso, você pode definir a segurança
por meio de comandos SQL padrão.
Portanto, há maneiras de definir
permissões por meio do próprio SQL
e, sob o capô, isso será mapeado para
permissões específicas do
IAM que se correlacionam com esses
comandos de permissão do SQL.
Você também pode usar o Amazon Lake
Formation
para gerenciar seu acesso em um nível mais
granular e fazer coisas como permissão de
consulta em nível de linha e coluna.
No lado da criptografia, você tem duas
opções: chaves gerenciadas
pelo S3 ou suas próprias chaves
gerenciadas pelo KMS.
Você pode escolher entre elas.
E outro ponto importante é o uso de
endpoints de VPC por meio do PrivateLink.
Portanto, se você precisar isolar esses
dados de alguma
forma, poderá configurar endpoints de
gateway e interface.
Os pontos de extremidade de interface são
apenas para
controle de nível de IP de granulação mais
fina.
O Gateway está realmente fazendo o
roteamento lá.
E você pode configurar diferentes
políticas de endpoint para
restringir o acesso por tabela ou por
bucket.
Há também endpoints de pilha dupla para
Ipv4 e IPv6, se você precisar deles.
E, a propósito, o acesso do público não
é permitido de forma alguma nas mesas S3.
Não é possível torná-los acessíveis ao
público, por mais que você tente.
Além disso, o HTTP não é permitido de
forma alguma.
Ele deve ser acessado por HTTPS.
