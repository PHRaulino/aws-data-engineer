Olá, e bem-vindos a esta palestra sobre o Amazon
Portanto, o EFS é um NFS gerenciado, que é um sistema de arquivos de rede.
E como é um sistema de arquivos
de rede, ele pode ser montado em várias instâncias
do EC2, e essas instâncias do EC2 também
podem estar em diferentes zonas de disponibilidade.
Portanto, é altamente
disponível, muito escalável e caro.
É cerca de três vezes o custo de um volume EBS GP2, e você paga por uso para
não precisar provisionar
a capacidade com antecedência.
Deixe-me explicar.
Portanto, você tem o sistema de arquivos
EFS e o envolve com um grupo de segurança.
E então você pode ter instâncias EC2, muitas delas na
zona de disponibilidade leste-1A dos EUA, por exemplo,
ou instâncias EC2 na zona de disponibilidade leste-1B dos EUA ou nas zonas
de disponibilidade leste-1C dos EUA para suas instâncias EC2.
E todos eles podem se conectar ao mesmo
tempo ao mesmo sistema de arquivos de rede por meio do EFS.
Portanto, os casos de uso do EFS são gerenciamento de conteúdo,
serviço na Web, compartilhamento de dados e WordPress.
Ele usa internamente o protocolo NFS e, para controlar
o acesso ao EFS, é necessário configurar
um grupo de segurança.
Agora, quanto ao EFS, é muito importante
observar que ele só é compatível com AMI baseada em
Linux e não com Windows.
Você pode ativar a criptografia em repouso
na unidade EFS usando o KMS, e ele é um sistema de arquivos padrão
no Linux, portanto, usa o sistema POSIX e tem uma API de arquivos padrão.
E o legal do EFS é que você
não precisa planejar a capacidade com antecedência.
O sistema de arquivos será dimensionado
automaticamente e é pago
por uso para cada gigabyte de dados que você usar no EFS.
Em seguida, temos diferentes classes de desempenho e armazenamento.
Então, primeiro, a escala sobre o EFS.
Você obtém milhares de clientes NFS simultâneos
e mais de 10 gigabytes de taxa de transferência, e pode
crescer automaticamente para um sistema
de arquivos de rede em escala de petabytes, o que é muito bom.
Também é possível definir o modo de desempenho
no momento da criação do sistema de arquivos de rede EFS, e você tem
várias opções.
O primeiro é de uso geral, que é o padrão.
É usado para casos de uso sensíveis à latência,
como um servidor da Web, um CMS, etc.
Mas, se você quiser maximizar a taxa de transferência, terá o max I/O, que
é um tipo de sistema de arquivos de rede de alta latência,
mas com maior taxa de transferência e altamente paralelo.
Portanto, é excelente se você tiver aplicativos de big
data ou necessidades de processamento de mídia.
Agora, no modo de taxa de transferência, você tem diferentes opções.
O primeiro está estourando.
Então, você tem um terabyte, o que significa
que são 50 megabytes por segundo mais
uma explosão de até 100 megabytes por segundo, portanto, esse é o
tipo de explosão que você obtém.
Você não precisa se lembrar dos números,
mas apenas para ter uma ideia.
Provisionado é quando você deseja definir sua taxa de transferência independentemente
do tamanho do armazenamento.
Portanto, o anterior estava aumentando a taxa de transferência à medida
que tínhamos mais armazenamento, mas com as provisões
você pode ter um gigabyte por segundo para um
terabyte de armazenamento.
Isso é bom porque você descorrelacionou a taxa de transferência
do seu armazenamento.
E, por fim, para simplificar um pouco as coisas, você
tem a elasticidade para aumentar e diminuir automaticamente a
taxa de transferência com base em sua carga de trabalho.
Assim, por exemplo,
você pode obter até três gigabytes por segundo para leituras
e um gigabyte por segundo para gravações com
base em sua carga de trabalho, e isso será
uma ótima opção quando você tiver cargas
de trabalho imprevisíveis.
Agora, para as classes de armazenamento, temos várias opções.
Temos níveis de armazenamento,
que é um recurso de gerenciamento de ciclo de vida que
permite mover arquivos para diferentes níveis de armazenamento
após um determinado número de dias.
Portanto, você tem a camada
padrão, que é usada para arquivos acessados
com frequência, e a camada EFS-IA para acesso pouco frequente, que oferece
um custo para recuperar arquivos, mas
um preço mais baixo para armazená-los.
E então você tem a camada de armazenamento de arquivos.
Isso é para dados raramente acessados, de modo que
você só acessa, por exemplo, dados algumas
vezes por ano, o que será muito mais barato para
armazenar os dados nessa camada.
Para mover seus arquivos automaticamente entre as camadas de armazenamento, você pode
implementar políticas de ciclo de vida, que permitirão
definir após quantos dias um arquivo
deve ser movido para qual camada.
Portanto, aqui está um exemplo em que temos arquivos
no padrão EFS e um desses arquivos não é acessado há 60 dias.
Em seguida, ao configurar a política de ciclo de vida
correta, podemos movê-lo para uma nova camada de armazenamento, como o EFS-IA.
Agora, em termos de disponibilidade e durabilidade,
o padrão será ótimo quando você tiver
uma configuração de várias zonas, portanto,
seu EFS em várias zonas de disponibilidade, o que é ótimo
para suas cargas de trabalho de produção, para que você
seja resistente a desastres.
Mas se você quiser apenas fazer desenvolvimento
e quiser ter opções mais baratas, escolha uma zona, que lhe
dará apenas uma zona de disponibilidade, e você ainda
terá backups nela, além de ser compatível
com o tipo de camada de armazenamento IA.
Portanto, você tem a opção do tipo EFS one zone-IA.
De modo geral, ao usar as classes de armazenamento EFS corretas,
você pode economizar até 90% dos custos,
o que é muito útil.
Então, é isso para esta palestra, espero que tenham
gostado e nos vemos na próxima palestra.
