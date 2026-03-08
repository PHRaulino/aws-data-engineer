Então, falando
para realmente transmitir estrutura aos seus dados não estruturados no
S3, de modo que ele possa realmente consultá-los como um banco de dados.
Então, novamente, vamos fazer uma breve recapitulação de como a cola funciona.
Você pode ter um rastreador do Glue preenchendo o
catálogo de dados do Glue para seus dados do S3 que está
analisando o que está armazenado no S3
e tentando extrair colunas
e definições de tabela para você.
E você pode usar o console Glue para
refinar essa definição conforme necessário.
Assim, quando você tiver um catálogo de dados do Glue
publicado para seus dados do S3, o Athena o verá automaticamente
e poderá criar uma tabela a partir dele também automaticamente.
Portanto, sempre que o Athena vir algo no catálogo de dados do Glue
em sua conta, ele criará
uma tabela para isso, para que você possa
consultá-la como faria com qualquer
outro banco de dados SQL.
E não é apenas o Athena que pode usar
esse catálogo de dados do Glue.
Isso permitirá que qualquer outra ferramenta de análise
visualize ou analise esses dados também.
Por exemplo, RDS, Redshift, Redshift Spectrum, EMR, qualquer aplicativo que
seja compatível com um Apache
Hive Metastore também, pois lembre-se de que o Glue Data
Catalog também pode ser usado como um Hive Metastore.
Mas, neste exemplo,
estamos usando-o para expor essa definição
de tabela ao Amazon Athena.
E com o Athena integrado ao Glue Data Catalog da AWS, você pode criar
um repositório de metadados unificado em vários
serviços, rastrear dados para descobrir esquemas, preencher seu
catálogo com definições de tabelas e partições
novas e modificadas e manter
o controle de versão do esquema, tudo isso sob o capô,
e o Athena fica em cima disso e fornece uma interface SQL para essa estrutura
Glue subjacente.
Outro recurso do Athena são os grupos de trabalho, e
você definitivamente precisa saber do que se trata.
Basicamente, é a forma, é o que parece.
É possível organizar usuários e equipes, ou
mesmo aplicativos e cargas de trabalho em diferentes
grupos de trabalho e agrupá-los.
E você pode usar isso para controlar o acesso à consulta de um determinado
grupo de trabalho ou para rastrear os custos
de um determinado grupo de trabalho.
Então, talvez você tenha uma equipe específica de pessoas
que só deve ter acesso a tipos específicos de consultas, ou
limites para as consultas que elas podem executar, certo?
E você quer acompanhar os custos individualmente
para descobrir que tipo de conta eles estão gerando
para a organização.
Os grupos de trabalho são integrados ao IAM, CloudWatch e SNS, para que
você possa fazer coisas como notificá-lo quando
os limites forem atingidos.
E a maneira de usar isso
é ter seus próprios limites de dados em cada grupo de trabalho.
Assim, você pode limitar a quantidade de dados que as consultas podem verificar por
grupo de trabalho.
Portanto, se quiser garantir que alguém de uma determinada
equipe não construa uma consulta extremamente ineficiente
que resulte em uma conta enorme, você pode
limitar isso no nível do grupo de trabalho.
Cada grupo de trabalho também tem seu próprio histórico individual de consultas.
Portanto, se você quiser garantir que uma equipe específica não veja as
consultas feitas por outra equipe, poderá dividi-las
em grupos de trabalho para garantir que
cada grupo de trabalho veja apenas
seu próprio histórico de consultas.
É claro que os grupos de trabalho também podem ter suas próprias políticas
de IAM, pois é assim que você gerenciará as permissões
e o que eles podem ver.
E você também pode ter suas próprias configurações de criptografia
em cada grupo de trabalho.
Portanto, é uma boa maneira de organizar muitas pessoas
em uma organização, limitar o que elas podem fazer e dar-lhes
permissões de acesso específicas usando
grupos de trabalho no Athena.
Portanto, lembre-se de que os grupos de trabalho do Athena são uma realidade.
Você pode usá-las para limitar o acesso
de um determinado grupo de pessoas ou para
medir o custo que elas estão fazendo e ter
limites para a quantidade de dados que as consultas
podem realmente verificar.
O modelo de custo é muito simples
porque é um aplicativo sem servidor.
Você só paga conforme a atividade
que realmente consome.
Atualmente, ele cobra US$ 5 por terabyte digitalizado, o que
é bastante generoso.
É importante lembrar que as consultas
bem-sucedidas ou canceladas contam para esse número digitalizado.
Você é cobrado por elas,
mas as consultas com falha não são cobradas.
Portanto, você será cobrado por qualquer consulta bem-sucedida ou cancelada.
No entanto, as consultas com falha são gratuitas.
Também não há cobrança de nenhuma operação DDL,
como CEEATE, ALTER ou DROP.
Elas também são gratuitas.
Agora, um ponto muito importante
é que, se você quiser economizar dinheiro usando
o Athena, poderá economizar muito dinheiro convertendo
seus dados em um formato colunar, como falamos
com o ORC e o Parquet.
Portanto, isso não só proporciona melhor desempenho
para aplicativos que normalmente consultam
um pequeno número de colunas, mas também
pode economizar de 30 a 90% em termos de dinheiro.
Isso porque ele permite que o Athena
leia seletivamente apenas as colunas necessárias ao fazer
uma consulta e processar seus dados.
Portanto, se você estiver acessando apenas determinadas colunas
de suas consultas por meio de uma coluna ou formato, estará reduzindo a quantidade
de dados que realmente precisa
verificar com o Athena.
E lembre-se, você é cobrado por terabyte de varredura.
Portanto, ao reduzir essa varredura, você ganha.
Portanto, lembre-se de que o Athena funciona melhor com formatos colunares.
Ele pode economizar muito dinheiro
e proporcionar um melhor desempenho.
Exemplos de formatos colunares incluem ORC e Parquet.
Tudo bem, e além da Athena, é claro, a Glue
e a S3 também têm suas próprias acusações.
O Athena fica em cima do Glue para obter a definição de tabela para os dados
do S3, e os dados continuam sendo armazenados no S3.
Portanto, há cobranças separadas para o Glue e
o S3, além do uso do Athena também.
Além disso, devo salientar que o particionamento de
seus dados também pode ajudar o Athena a reduzir os custos.
Portanto, se você tiver seus dados
estruturados no S3 em diferentes
partições, como por data, hora ou algo assim, as consultas
restritas a essa partição também examinarão menos
dados.
Portanto, além de usar um formato colunar, o particionamento
de seus dados no S3 também pode economizar dinheiro
com o Athena.
Vamos falar sobre segurança também.
Isso é sempre importante com a Athena.
Ele oferece muitas maneiras
diferentes de proteger seu tráfego do Athena.
Uma delas é por meio do controle
de acesso, ou seja, quem pode realmente acessar
o Athena e consultar suas informações em primeiro lugar.
E você pode usar o IAM, as listas de controle de acesso
e as políticas de bucket do S3 para restringir
o acesso a essas informações.
As políticas de IAM que são relevantes aqui
são as políticas AmazonAthenaFullAccess
e AWSQuicksightAthenaAccess.
Você também pode criptografar
seus resultados se for sensível aos resultados de suas
consultas, e pode criptografá-los
em repouso em um diretório de preparação no S3.
E isso pode ser criptografado de várias maneiras diferentes.
Mais uma vez, é importante lembrar disso, pessoal.
Portanto, você pode criptografar os resultados dos dados
do S3 na criptografia no lado do servidor usando uma
chave gerenciada pelo S3 chamada SSE-S3.
Você também pode fazer a criptografia dos
resultados no lado do servidor usando uma chave KMS.
Isso é chamado de SSE-KMS, ou você também
pode criptografá-los no lado do cliente
com uma chave KMS.
Isso é chamado de CSE-KMS.
E, dependendo de seus requisitos de segurança, uma
ou mais dessas opções podem fazer sentido.
Portanto, pense em como esses dados estão fluindo, onde
estão sendo armazenados e como você deseja que eles sejam protegidos.
Você também pode ter acesso a várias contas para encontrar
uma política de bucket S3.
Portanto, é possível acessar o Athena em um bucket S3 que não
pertence à sua conta.
Se esse outro bucket S3 tiver uma política que conceda acesso
à sua conta, é possível
que um console Athena em uma conta acesse um data
lake armazenado em outra conta.
Você pode configurar isso.
Quanto à segurança em trânsito,
você pode usar o TLS, Transport Layer Security,
para todo o tráfego entre o Athena e o S3.
Isso também pode ser configurado para segurança em trânsito com o Athena.
É sempre importante lembrar os aspectos de
segurança, pois essa é uma grande parte do exame.
Por fim, vamos falar sobre antipadrões.
Mais uma vez, essas informações
foram retiradas diretamente do white paper de big data da AWS sobre as coisas para as quais
eles não querem que você use o Athena.
Um deles é para relatórios altamente formatados ou para visualização.
No final das contas, o Athena é apenas um mecanismo de consulta SQL.
Se você quiser fazer coisas bem formatadas ou
visualizar coisas com tabelas e gráficos,
bem, é para isso que serve o QuickSight,
que será abordado em breve.
Além disso, se você quiser fazer operações de ETL, extração,
transformação e carregamento usando o
Athena, essa geralmente não é a melhor ferramenta a ser usada.
A cola é uma alternativa.
E, em vez disso, usando o Glue ETL, você também pode
fazer isso com o Apache Spark ou o que for necessário
para tarefas de maior escala.
Então, essa é a Athena em poucas palavras.
Vamos brincar com ele, certo?
