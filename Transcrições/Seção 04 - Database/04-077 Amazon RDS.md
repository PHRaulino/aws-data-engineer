Vamos falar
o Serviço de Banco de Dados Relacional.
Isso não é realmente relevante para o big data.
Na verdade, é mais para dados
pequenos, mas isso aparecerá
no exame e você precisará saber o que é,
em geral, uma espécie de exemplo do
que não fazer, ou talvez um exemplo
de como importar seus dados RDS
para um sistema de big data maior.
O que é RDS?
Bem, ele é um banco de dados relacional hospedado,
que pode ser qualquer um dos
seguintes tipos de banco de dados.
Amazon Aurora, sobre o qual falaremos em breve.
Você também pode hospedar um banco
de dados MySQL, um banco de dados PostgreSQL, MariaDB,
que é basicamente uma versão de
código aberto do MySQL, Oracle ou Microsoft SQL Server.
Portanto, é uma forma de fazer com que o AWS hospede seu próprio
host de banco de dados, para que você não
precise se preocupar em manter esse host de banco
de dados por conta própria, o que, como todos sabemos,
ser um DBA nem sempre é uma coisa divertida, mas é uma coisa
útil.
Mas não se trata de big data.
Como eu disse, ele pode aparecer
no exame como um exemplo do que
não usar em um problema de big data, ou no
contexto da migração do RDS para o Redshift ou
algo do gênero.
Ele foi criado para necessidades
menores, nas quais você
pode usar um único host de banco de dados e armazenar
todos os seus dados nele.
Por exemplo, eu uso o RDS e o Amazon Aurora para
fazer o backup dos meus sites.
Portanto, para o WordPress, ele está usando o RDS
como armazenamento de backup para isso.
Um bom momento para falar sobre a conformidade com o ACID.
Isso ocorre com frequência no
mundo dos bancos de dados relacionais em geral,
e todos os bancos de dados RDS oferecem
total conformidade com ACID.
Portanto, se você precisar de um banco de dados
que atenda a esses requisitos, o
RDS pode ser uma solução, desde que você não
precise de conjuntos de dados enormes
que não caibam em um único host.
Agora, sob o capô, ele pode realmente estar
usando mais de um host.
Isso tudo é uma espécie de caixa preta
para nós, mas ainda faz sentido pensar no RDS
mais como uma solução de dados pequenos.
ACID, de qualquer forma,
significa Atômico, Consistente, Isolado e Durável.
E apenas uma pequena atualização para vocês.
Portanto, a atomicidade garante que a transação
como um todo seja executada com êxito
ou, se parte de uma transação falhar,
toda a transação será invalidada.
Portanto, se você estiver enviando
uma transação que faz mais de
uma coisa, se alguma parte
dela falhar, a transação inteira será descartada.
A consistência garante que os dados gravados
no banco de dados como parte da transação devem
obedecer a todas as regras e restrições
definidas, inclusive restrições, cascatas
e acionadores.
O isolamento garante que cada transação seja
independente de si mesma, o que é fundamental para
obter o controle de simultaneidade.
Por fim, a durabilidade garante que todas
as alterações feitas no banco de dados sejam permanentes após
a conclusão bem-sucedida de uma transação.
Vamos falar um pouco sobre o Amazon
Aurora, que é outra opção para RDS.
Ele oferece suporte a bancos
de dados MySQL e PostgreSQL.
Assim, por exemplo, se você quisesse
fazer o backup do seu próprio site WordPress ou algo
do tipo com o Amazon Aurora, poderia
fazer isso e, no que diz respeito ao
WordPress, ele se pareceria com o MySQL.
Portanto, é uma alternativa hospedada
para o MySQL e o PostgreSQL.
E, de acordo com o discurso de marketing
da Amazon Web Services,
ele é até cinco vezes mais rápido que o MySQL e três
vezes mais rápido que o PostgreSQL.
É claro que sua milhagem pode variar.
Na verdade, talvez não seja possível obter esses
ganhos exatos.
Isso é uma espécie de discurso de marketing, mas é mais rápido.
Também é barato.
Ele pode custar até 1/10 do custo
dos bancos de dados comerciais.
No entanto, é uma comparação injusta, pois
o MySQL não é um banco de dados comercial, certo?
Então, eles estão basicamente
dizendo que, em comparação
com a Oracle ou algo
do gênero, será muito
mais barato, mas usar apenas o MySQL de código aberto
também seria muito mais barato.
O limite atual de armazenamento
é de até 128 terabytes por volume de banco de dados.
Portanto, observe que o armazenamento
é desacoplado da instância real do Aurora
e também oferece até 15 réplicas de leitura.
Portanto, se você precisar de maior desempenho,
poderá usar réplicas de leitura para obter acesso
mais rápido, distribuído e dimensionável aos dados
subjacentes.
Esse é um bom recurso.
E isso também diminui o tempo de replicação para milissegundos.
Isso também é muito útil.
Ele também oferece backup contínuo para o S3, para que você
nunca precise se preocupar
com a perda de seus dados, e também
oferece replicação entre regiões e zonas de disponibilidade.
Portanto, você pode replicar
seus dados em todo o mundo, como quiser.
Ele também oferece um serviço mais
novo, devo dizer, chamado Aurora Serverless.
Portanto, se você não quiser dedicar hardware
a ele e pagar por esse hardware durante todo o mês,
se tiver um tráfego mais dinâmico e inconsistente para o seu banco de
dados, o Aurora Serverless pode ser uma
opção melhor para você.
Isso oferece escalonamento automático de acordo com o seu tráfego,
em vez de apenas pagar por um servidor, um host de banco de dados
que fica lá o tempo todo esperando
por você e que pode ou não
estar sendo usado.
Mas se você tiver um caso de uso em que o banco de dados é acessado
de forma consistente 24 horas por dia, 7 dias por semana, provavelmente
será melhor usar uma instância
de banco de dados dedicada.
Mas, com o Aurora, você tem
a opção de ter seu próprio banco de dados.
Mas você tem a opção de escolher com o Aurora.
Você pode usar seu próprio
host de banco de dados dedicado
ou pode usar o Aurora Serverless e ter essa capacidade
ampliada automaticamente.
No que diz respeito à segurança com o Aurora,
ele oferece isolamento de rede VPC, obviamente.
Ele também pode fazer a criptografia em repouso usando o KMS.
Portanto, os dados, o backup, os instantâneos
e as réplicas podem ser criptografados e
ele também pode fazer a segurança em trânsito usando SSL.
Em resumo, esse é o Aurora e o RDS.
Mais uma vez, geralmente não no contexto de big
data, mas o Aurora está tomando direções
interessantes, portanto, ficaremos atentos
a isso no futuro.
