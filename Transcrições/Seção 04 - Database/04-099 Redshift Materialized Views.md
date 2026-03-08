Você também
Vamos falar sobre o que são esses recursos no Redshift.
Então, você sabe o que é uma visualização em um banco
de dados: basicamente, ela pega os resultados de uma consulta e faz
com que se pareçam com outra tabela que você
pode consultar posteriormente.
Uma visualização materializada é um pouco diferente.
Portanto, na verdade, ele está pré-computando os resultados
dessa consulta, armazenando-os e fazendo
com que pareçam outra tabela.
Portanto, ela é diferente de uma visualização normal,
se preferir, pois está armazenando os resultados da consulta
e não apenas a consulta em si.
Portanto, como você pode ver, essa pode ser uma otimização de
desempenho muito importante.
Portanto, se você tiver uma consulta complexa em seu data warehouse
em uma tabela grande, poderá consultar essa visualização materializada
como qualquer outra tabela ou visualização
com base nos resultados salvos de uma consulta mais complexa.
Portanto, se você precisar criar uma consulta
sobre uma consulta mais complicada, poderá armazenar os resultados
dessa consulta complicada em uma
visualização materializada e, em seguida,
consultar esses resultados repetidamente em outras consultas.
Portanto, como você está usando esses resultados pré-computados
e não está acessando as tabelas de base, isso pode
ser uma otimização de desempenho muito importante.
É claro que isso tem o custo
de ter um problema de sincronização.
Portanto, se os resultados da sua visualização materializada mudarem porque
o material subjacente que você está consultando mudou, essa visualização
materializada precisará ser explicitamente
atualizada de alguma forma.
Um exemplo de como você pode querer usar
isso é se tiver uma consulta previsível e recorrente,
como preencher um painel do Amazon QuickSight ou algo parecido.
Portanto, se você sabe que seu painel
precisará dos resultados de um determinado conjunto de consultas,
talvez seja possível pré-computar esses resultados
usando visualizações materializadas e,
em seguida, criar seu painel com base
nessa visualização materializada para torná-lo mais eficiente,
em vez de executar essa consulta
sempre que quiser ver seu painel.
Como posso usá-los? Eles são muito fáceis.
Portanto, em vez de criar uma
visualização, basta dizer "criar uma visualização materializada" e pronto.
Portanto, em vez de uma visualização baseada na consulta,
você está criando um instantâneo dos resultados dessa consulta e
criando uma visualização a partir dele.
Como faço para mantê-los atualizados?
Então, como eu disse, há um problema de sincronização
porque estou armazenando os resultados
e não apenas a consulta em si.
Pode haver um problema de sincronização
em que os dados subjacentes aos quais estou consultando essa visualização
materializada mudam.
Portanto, para manter a visualização materializada sincronizada
com essas alterações, posso atualizá-la manual e explicitamente
quando necessário, usando o comando refresh materialized view.
Você também pode definir a opção de atualização
automática ao criá-lo
para que isso aconteça automaticamente.
Portanto, depende de quanto controle você deseja ter sobre ele.
Se quiser ter controle sobre a frequência com
que ele é atualizado para manter o desempenho, talvez
seja necessário atualizá-lo apenas uma vez por dia, pois você
o usará para um painel
que é consultado uma vez por dia.
Então, talvez seja possível atualizar essa visualização materializada
apenas uma vez por dia, em vez de atualizá-la
automaticamente sempre que algo mudar.
Depois de ter uma visualização materializada,
você pode consultá-la como qualquer outra tabela ou visualização.
Ele se parece com qualquer outra coisa,
e você também pode empilhá-los uns sobre os outros.
Assim, você pode ter visualizações materializadas
que são criadas a partir de outras visualizações materializadas,
o que é muito legal.
Um exemplo de como isso pode ser útil é que,
se você tiver alguma operação JOIN cara entre várias
tabelas, poderá armazenar os resultados dessa JOIN como uma visualização
materializada e, em seguida, ter outras visualizações
materializadas que tenham consultas específicas
usando esses dados unidos.
Portanto, você pode empilhá-los uns sobre os outros,
o que também pode ser usado para acelerar o desempenho da consulta.
