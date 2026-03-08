Este exame se concentra em operações e engenharia
Portanto, vamos falar sobre algumas práticas recomendadas do
RDS em operações para otimizar o desempenho
de seu banco de dados e sua estabilidade operacional.
A dica número um é usar o CloudWatch
para ficar de olho na memória,
no armazenamento da CPU e no atraso da réplica em suas instâncias RDS.
Nem é preciso dizer que você
deve usar o CloudWatch, certo?
Se você estiver se preocupando
com o desempenho de qualquer
sistema, não apenas com o RDS.
E se você for fazer backups automáticos, tente
fazer isso durante o período do dia
em que o IOPS de gravação for mais baixo.
Se estiver tentando fazer backup
de algo enquanto ele ainda está sendo gravado ativamente,
isso se torna complicado.
E não fique apenas tentando adivinhar.
Não diga simplesmente: "Bem, ninguém acessa meu banco de dados às
2h da manhã. Não, use
as métricas do CloudWatch para descobrir
isso e baseie-se em dados reais.
Esteja ciente de que uma capacidade de E/S insuficiente em
suas instâncias causará problemas se você
precisar se recuperar após uma falha.
Portanto, a última coisa que você quer é
ter um banco de dados inoperante e descobrir
que está tendo dificuldades para
mudar para uma instância de backup
porque sua capacidade de E/S é insuficiente para
fazer esse failover.
Portanto, certifique-se de que as instâncias do seu banco de dados tenham a quantidade
de E/S necessária.
Talvez você precise migrar para um com mais.
Uma maneira de obter melhor capacidade
de E/S é mudar para o armazenamento de propósito geral ou IOPS
provisionado para suas instâncias RDS.
Além disso, se você tiver aplicativos que atingem o banco de dados
RDS, certifique-se de que o tempo de vida do DNS
para esse banco de dados esteja definido para 30 segundos ou menos.
Mais uma vez, você não quer estar em uma situação
em que precise fazer failover do seu banco de dados
e das suas estratégias de failover para alterar a entrada de
DNS de um host para outro e depois descobrir
que o DNS está sendo armazenado em cache por uma hora, certo?
Portanto, em vez de fazer a troca em 30 segundos, agora
você tem que ficar parado por uma
hora enquanto o cache é para o DNS no tempo limite do seu aplicativo.
Portanto, não deixe de pensar no tempo de vida
útil do DNS para o seu banco de dados se você pretende
usar o DNS como mecanismo de failover.
E teste seus failovers antes de precisar deles.
Você sabe que não quer descobrir isso
quando estiver sob pressão porque as coisas derreteram
e seus aplicativos não estão mais funcionando.
Na Amazon, costumávamos chamar isso de dia do jogo.
Simularíamos uma falha maciça de tudo na Amazon em
um ambiente de teste e praticaríamos
como lidar com isso.
Portanto, é uma boa ideia praticar o failover
antes de precisar fazê-lo de fato.
Certifique-se de ter RAM suficiente provisionada
em suas instâncias RDS para incluir todo o seu conjunto de trabalho.
Novamente, você não precisa adivinhar isso.
Você pode monitorar a métrica ReadIOPS.
E se essa métrica for pequena e estável, isso significa
que você não está atingindo muito o disco.
Portanto, você provavelmente tem RAM suficiente para incluir seu conjunto de trabalho.
No entanto, se não estiver estável e for
mais alto do que o esperado, isso provavelmente
significa que você está usando o disco mais do que deveria
e precisa de mais RAM.
Além disso, se os seus dados no RDS estiverem sendo expostos externamente por meio
de um aplicativo, de alguma forma, para o mundo exterior ou para um
site, talvez seja melhor pensar em impor limites de taxa
no gateway de API da Amazon para proteger seu banco de dados.
Portanto, se você quiser proteger seu banco
de dados contra negação de servidores, ataques e coisas do gênero, poderá
configurar um limite de taxa no gateway de
API para garantir que ninguém possa atingir seu aplicativo
mais do que uma frequência razoável para
a qual você foi projetado.
Além disso, para melhorar o desempenho
no RDS, você pode otimizar suas consultas.
A regra básica de otimização de consultas é usar índices sempre que possível.
Portanto, sempre que você tiver uma instrução select, certifique-se
de analisar suas consultas
e de ter os índices necessários para torná-las eficientes.
E, se não tiver certeza,
poderá usar os planos de explicação para identificar
quaisquer índices que possam ser necessários para
dar suporte a essa consulta.
Outra forma de dizer a mesma coisa é
evitar a varredura completa da tabela.
Portanto, se você estiver fazendo uma varredura completa
da tabela, isso significa que há algo errado com sua consulta
ou que você não tem um índice que realmente
deveria ter, certo?
Portanto, as varreduras de tabelas completas são ruins.
Os índices são a maneira de evitá-los.
De vez em quando, use o comando analyze table para
se certificar de que a tabela em si está em boas condições.
Se você tiver cláusulas where,
tente torná-las o mais simples possível.
Eles podem causar muitas despesas gerais.
Além disso, há algumas otimizações específicas do
mecanismo sobre as quais falaremos a seguir.
Portanto, no MySQL e no MariaDB, aqui estão algumas dicas específicas.
Uma delas é manter suas tabelas bem abaixo de 16 terabytes
e, idealmente, abaixo de 100 gigabytes.
Caso contrário, você poderá ter problemas
de desempenho com o MySQL e seu primo próximo, o MariaDB.
Certifique-se de que você tenha memória
RAM suficiente para manter os índices das tabelas usadas ativamente.
Tente ter menos de 10.000 tabelas, pois
mais do que isso pode causar problemas.
E para sua escolha de mecanismo de armazenamento,
o AWS recomenda o uso do InnoDB.
Se você estiver usando o PostgreSQL, há algumas dicas
para quando estiver carregando dados no
PostgreSQL inicialmente.
Aparentemente, isso pode ser lento.
Portanto, certifique-se de desativar os backups de banco de
dados e também os recursos multi-AZ enquanto
estiver fazendo o carregamento massivo inicial
no PostgreSQL.
Além disso, há parâmetros específicos que podem ser ajustados
para que isso aconteça mais rapidamente.
Eu ficaria surpreso se elas aparecessem no exame, mas
algumas são óbvias, como garantir que o vácuo automático esteja desligado
durante essa operação.
Portanto, a conclusão é que o carregamento de dados
no PostgreSQL pode ser lento.
Há algumas coisas específicas que você precisa
fazer para acelerar esse processo.
No entanto, quando não estiver carregando
dados, o autovacuum deve estar ativado.
Isso será importante
para manter o desempenho no futuro.
E, finalmente, para o SQL Server, certifique-se
de estar usando o RDS DB Events para ficar de olho
em qualquer failover que possa
estar ocorrendo no SQL Server.
Além disso, se estiver usando o SQL
Server em um ambiente de zona de disponibilidade multi-AZ,
não ative o modo de recuperação simples, o modo off-line
ou o modo somente leitura.
Tudo isso interromperá uma implantação em várias AZs.
Portanto, é importante lembrar.
E eles recomendam que você implante o SQL Server em todas
as zonas de disponibilidade para fins de redundância e para garantir que as
coisas continuem funcionando da melhor forma possível.
Por fim, se você estiver usando
o Oracle, bem, esse é um caso à parte.
A otimização no Oracle poderia ser o assunto
de um curso inteiro e eu realmente
duvido que eles entrem em
detalhes sobre isso porque, bem, as pessoas
geralmente usam as opções de código aberto
no RDS atualmente.
Portanto, essa é a otimização do RDS em poucas palavras.
Alguns pontos a serem lembrados para o exame.
