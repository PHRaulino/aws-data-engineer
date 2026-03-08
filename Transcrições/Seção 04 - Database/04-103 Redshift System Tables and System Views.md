sobre as tabelas e visualizações do sistema Redshift.
Como acontece com a maioria dos bancos de dados
relacionais, você pode obter informações sobre o próprio sistema
consultando suas tabelas e exibições mantidas internamente,
que estão lá automaticamente
para você.
Portanto, eles contêm informações
sobre como o próprio Redshift está funcionando.
Portanto, em um nível muito alto, há diferentes
tipos de tabelas e visualizações do sistema, e vamos
apenas analisar esse nível alto,
pois há muitas tabelas e visualizações individuais para
analisar aqui.
Você só precisa saber
o que eles são e para que servem, certo?
Portanto, há visualizações
de sistema que começam com SYS.
Essas são as exibições do SYS
e são usadas para monitorar a consulta e o uso
da carga de trabalho, principalmente.
Há também tabelas de sistema que começam com STV, que monitoram
dados transitórios, contendo instantâneos
dos dados atuais do sistema.
Além disso, há exibições SVV que
contêm metadados sobre objetos do banco
de dados que fazem referência a essas tabelas STV.
Há também visualizações STL.
Elas são geradas a partir de registros que são mantidos em
disco e, em seguida, há exibições SVCS,
que são detalhes sobre consultas nos clusters
principal e de dimensionamento de simultaneidade.
Para consultas específicas sobre os clusters principais,
as visualizações SVL terão essas informações.
E as tabelas e exibições específicas que
estão disponíveis variam de acordo com o
fato de você estar usando uma instância de provisionamento
ou uma instância sem servidor,
mas elas têm muito em comum.
Vamos dar uma olhada neste exemplo à direita.
Este é um exemplo
em que estamos analisando o tempo de execução de consultas recentes.
Então, se analisarmos isso
aqui, podemos ver que estamos obtendo isso do stl_query, certo?
Portanto, stl_query é uma visualização STL.
Isso significa que é gerado a partir de registros persistentes
no disco, e estamos juntando isso ao svl_qlog.
Novamente, o SVL contém detalhes sobre consultas nos clusters principais, portanto,
o svl_qlog provavelmente seria o registro de consultas, certo?
Estamos fazendo uma junção entre esses dois,
com base no campo de consulta.
Portanto, estamos unindo svl_qlog com stl_query
para obter essas consultas recentes e dizendo especificamente
que estamos fazendo uma cláusula WHERE para
obtê-las no último dia, certo?
Assim, ao obter essas informações sobre consultas recentes,
podemos selecionar os atributos dessas consultas,
como a hora de início, a hora de término,
quanto tempo levou, vamos computar isso e
computar o tempo de execução usando o comando DATEDIFF e o status disso
no final.
Portanto, apenas um exemplo de uso de tabelas e exibições
do sistema para obter algumas informações sobre o desempenho
do Redshift para você.
Portanto, lembre-se de que eles estão lá para
você e para que podem ser usados.
