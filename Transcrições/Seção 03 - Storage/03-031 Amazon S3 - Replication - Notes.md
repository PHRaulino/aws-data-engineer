Ei, apenas algumas observações
Portanto, depois de ativar a replicação, como
você viu, somente os novos objetos serão replicados.
E se você quiser replicar objetos existentes,
precisará usar o recurso S3 Batch Replication.
Portanto, isso replicará os objetos existentes e os
objetos que falharam na replicação e, caso você
tenha operações de exclusão, poderá replicar esses marcadores
de exclusão do bucket de origem para o bucket
de destino.
É uma configuração opcional, mas, se você tiver uma exclusão
com o ID da versão, ela não será replicada, portanto,
se for uma exclusão permanente,
você deve evitar que ocorram exclusões mal-intencionadas
de um bucket para outro.
Por fim, não há encadeamento de réplicas.
Isso significa que, se o bucket
um tiver replicação para o bucket
dois e, em seguida, o bucket dois tiver replicação
para o bucket três, os objetos
do bucket um não serão replicados no bucket três.
Espero que tenham gostado e nos veremos na próxima palestra.
