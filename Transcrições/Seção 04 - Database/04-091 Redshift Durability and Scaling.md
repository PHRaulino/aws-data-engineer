Agora vamos falar sobre as
O Redshift replica todos os dados no cluster
do data warehouse quando ele é
carregado automaticamente.
Além disso, o backup dos seus dados é feito continuamente no S3 para você.
Três cópias dos dados são mantidas:
no original, em uma réplica nos nós de computação
e em um backup no S3.
Portanto, seus dados são armazenados em três locais diferentes.
Há a cópia original em seu cluster, há uma
cópia de réplica de backup também em seu cluster e,
além disso, ele faz backups periódicos no S3 para você.
Portanto, para a recuperação de desastres,
o Redshift replica de forma assíncrona seus instantâneos para
o S3 em outra região também.
Ele pode ativar instantâneos automatizados
do cluster do data warehouse
com um período de retenção de um dia por padrão; você pode
estender esse período de retenção para até 35 dias, se desejar.
No entanto, se você reduzir o período de retenção para
zero, os backups automatizados serão desativados.
Agora, se você precisar restaurar o cluster a partir de
um backup, basta escolher um dos backups automatizados
e, em seguida, o AWS provisionará um novo cluster de data warehouse e restaurará
seus dados para ele.
Em seguida, você pode mudar do cluster antigo para
o recém-restaurado.
O Redshift replica os dados
no cluster do data warehouse
e faz o backup contínuo desses dados no S3.
Ele também espelhará os dados de cada unidade para
os outros nós do cluster.
O Redshift detectará automaticamente uma unidade ou um nó com
falha e o substituirá automaticamente para você.
No caso de uma falha na unidade, o cluster
do Redshift permanecerá disponível com uma ligeira
queda no desempenho de determinadas consultas enquanto o Redshift
reconstrói essa unidade a partir de uma réplica dos dados
nessa unidade, que é armazenada em
outra unidade dentro desse nó.
Os clusters de nó único não são compatíveis com a replicação de
dados, pois não há nada para onde replicá-los.
Nesse caso, você teria que restaurar
o cluster a partir de um instantâneo no S3.
No caso de uma falha de nó individual, o Redshift
detectará automaticamente essa falha de nó e substituirá
um nó com falha em seu cluster de data warehouse.
Agora, até que esse nó substituto seja provisionado
e adicionado ao banco de dados,
o cluster não estará disponível para consultas e atualizações.
Os dados acessados com mais frequência do S3,
no entanto, são carregados primeiro no novo
nó, para que você possa retomar a consulta desses dados o mais rápido possível.
Os clusters de nó único não oferecem suporte
à replicação de dados e, portanto,
você precisará restaurar
o cluster a partir de um instantâneo no S3 no caso de uma
falha de nó em um cluster de nó único.
Agora, no caso de uma interrupção
da zona de disponibilidade do cluster do Redshift,
nesse caso, você não poderá usar
o cluster até que a energia e o acesso à rede da zona de
disponibilidade sejam restaurados, porque
o Redshift está atualmente limitado a uma única zona
de disponibilidade; no entanto, você pode
restaurar o cluster de qualquer snapshot
existente para uma nova zona de disponibilidade na mesma região.
Portanto, também nesse caso, os dados acessados com mais frequência
serão restaurados primeiro do S3, para que você possa
retomar suas consultas o mais rápido possível.
A Amazon está trabalhando para remover essa restrição,
no entanto, a partir de novembro de 2022,
eles anunciaram o suporte a zonas de indisponibilidade
múltipla, especificamente para clusters RA3.
Como o Redshift é dimensionado?
Bem, os clusters do Redshift suportam tanto a escala
vertical, que é o aumento do tipo de instância
do nó, quanto a horizontal, que é o aumento do número
de nós.
As alterações solicitadas serão aplicadas imediatamente
quando você modificar o cluster do data warehouse.
Veja como o processo funciona.
Portanto, quando você estiver
dimensionando, um cluster de data warehouse existente permanecerá
disponível para operações de leitura
e um novo cluster de data warehouse será criado durante
as operações de dimensionamento.
Quando esse novo cluster estiver pronto, o cluster
existente ficará temporariamente indisponível.
Enquanto um registro CNAME para o cluster existente
é invertido para um ponto no novo cluster de data warehouse.
Isso leva apenas alguns minutos
e geralmente é feito durante algum tipo
de janela de manutenção.
O Redshift moverá os dados dos nós de computação
no cluster de data warehouse existente
em paralelo para os nós de computação no novo cluster.
