Em seguida, temos o S3 storage
analisar e otimizar o armazenamento em toda a sua organização AWS.
Com isso, você descobrirá anomalias,
identificará eficiências de
custo e aplicará as práticas recomendadas de
proteção em toda a sua organização da AWS.
Você obterá métricas de uso e atividade de 30 dias.
Você pode agregar os dados no nível da organização ou para contas,
regiões, compartimentos ou até mesmo prefixos
específicos.
Você pode criar seu próprio painel ou usar um painel padrão fornecido
pelo serviço de lente de armazenamento.
E, por fim, todas essas métricas
e todos esses relatórios podem ser exportados para um bucket
S3 no formato CSV ou Parquet.
Portanto, para resumir, a
lente de armazenamento levará todos esses aspectos em consideração:
organização, contas, região, compartimentos.
Em seguida, você agrega todos esses dados em um relatório,
que o ajudará na análise.
E, finalmente, isso pode ser enviado para obter insights
resumidos, proteção de dados, eficiência
de custos, o que permite otimizar o uso do Amazon S3.
Portanto, ao usar o serviço de lente de armazenamento
S3, você tem um painel padrão, que
fornece insights e tendências resumidos
para as métricas gratuitas e avançadas.
Esse painel padrão mostrará dados
de várias regiões e de várias contas.
Portanto, você não precisa fazer nada
de especial apenas para configurar os filtros.
Ele é pré-configurado pelo Amazon S3.
Você não pode excluir o painel padrão,
mas pode desativá-lo se quiser.
Portanto, nesta interface do usuário,
você selecionaria a região desejada, as contas desejadas,
os buckets desejados, as classes de armazenamento e assim por
diante, e essa é uma configuração centralizada.
Depois disso, o painel
aqui fornece informações como, por
exemplo, o armazenamento total, a contagem de objetos,
o tamanho médio dos objetos,
o número de buckets que você tem, contas,
e você pode obter detalhes por contas ou por região.
Portanto, vamos dar uma olhada nos tipos de
métricas disponíveis na lente de armazenamento,
pois isso o ajudará a entender se a lente de armazenamento
é um serviço que você deve escolher para o exame.
Portanto, você tem métricas resumidas
que fornecem informações gerais sobre o armazenamento S3.
Por exemplo, StorageBytes, para saber o tamanho de seu armazenamento, e contagem
de objetos, para saber quantos
objetos você tem em seu armazenamento.
Portanto, os casos de uso para isso são para identificar,
por exemplo, o bucket e os prefixos que crescem mais rapidamente ou que não são usados.
Porque se o StorageBytes permanecer o mesmo,
isso significa que nenhum objeto novo foi adicionado
ou o mesmo para o ObjectCount.
Em seguida, você tem métricas de otimização de custos.
Além disso, eles fornecem insights para gerenciar
e otimizar o custo de armazenamento.
Portanto, eles fornecem informações
sobre o NoncurrentVersionStorageBytes.
Ou seja, quantos objetos de versão não estão atualizados, quanto espaço
eles estão realmente ocupando, ou IncompleteMultipartUploadStorageBytes
para saber se, por exemplo, você teve alguns uploads incompletos,
quanto espaço eles ocupam no seu bucket e você pode limpá-lo.
Portanto, os casos de uso serão, por exemplo,
para ver quais buckets falharam em uploads de várias partes ou quais objetos
poderiam ser transferidos para classes de
armazenamento de custo mais baixo.
Você tem métricas de proteção de dados para fornecer insights
sobre os recursos de proteção de dados.
Portanto, aqui temos VersioningEnabledBucketCounts para garantir
que todos os seus buckets tenham sido ativados com controle de versão
e assim por diante.
MFADeleteEnabledBuckeCount, SSEKMSEnabledBucketCount,
CrossReplicationRegionRulesCount e assim por diante.
Portanto, os casos de uso são, por exemplo, para identificar os compartimentos
que não estão seguindo suas práticas recomendadas de proteção de dados.
Você tem métricas de gerenciamento de acesso para fornecer insights
sobre a propriedade do bucket S3.
Então, aqui está o nome da métrica.
E os casos de uso serão identificar quais
configurações de propriedade de objeto seus buckets usam atualmente.
Você tem métricas de eventos para obter
insights sobre as notificações de eventos
do S3 e saber quantos buckets têm as notificações
de eventos do S3 configuradas.
Você tem métricas de desempenho
para obter insights sobre a aceleração de transferência do S3 e ver
quantos buckets têm a aceleração de transferência
do S3 ativada.
E você tem métricas de atividade,
como informações sobre AllRequests, GetRequests, PutRequests,
o número de bytes baixados e assim por diante.
E, por fim, métricas sobre o código de status HTTP, como
200OK, 403Forbidden, etc., para entender o tipo
de uso que seus buckets estão recebendo.
Agora, você tem diferentes tipos de métricas nas lentes de
armazenamento, as métricas gratuitas e as pagas.
Portanto, a seleção de métricas também pode ser feita na interface do usuário.
Mas, apenas como um resumo, enquanto as métricas gratuitas
estão automaticamente disponíveis para todos
os clientes, elas contêm cerca de 28 métricas de uso e os dados estão
disponíveis para consultas por 14 dias.
Já para as métricas e recomendações avançadas,
você obtém métricas e recursos adicionais
pagos, como a atividade, a otimização avançada de custos, a proteção avançada
de dados e os códigos de status.
Além disso, essas métricas também
são publicadas no CloudWatch.
Assim, você pode acessá-los sem nenhum custo adicional.
E, em seguida, você pode coletar métricas no nível do
prefixo em seus buckets S3.
E, por fim, os dados, quando você
paga, ficam disponíveis por 15 meses.
Isso é tudo para a lente de armazenamento S3.
É um serviço muito útil.
É preciso lembrar a diferença entre gratuito e pago.
Você deve se lembrar de que o painel
padrão tem dados de várias contas e várias regiões.
E, é claro, o fato de que a lente de
armazenamento cobre o armazenamento de objetos, o fato
de que você pode contar quantos objetos estão criptografados
e assim por diante.
Então, digamos que, para esta palestra, espero
que você tenha gostado e nos vemos na próxima palestra.
