Agora vamos falar sobre a replicação
Portanto, CRR é para replicação entre regiões
e SRR é para replicação na mesma região.
A ideia é que temos um S3 Bucket em
uma região e um S3 Bucket de destino em outra
região, e queremos configurar a replicação assíncrona
entre esses dois buckets.
Portanto, para fazer isso, primeiro precisamos ativar o controle
de versão nos buckets de origem e de destino.
E se fizermos CRR, ou seja, replicação entre regiões, as duas regiões
devem ser diferentes.
Se fizermos o SRR, as duas regiões serão as mesmas.
Agora, é possível ter esses buckets
em diferentes contas do AWS e a cópia
acontece de forma assíncrona.
Portanto, o mecanismo de replicação acontece nos bastidores,
em segundo plano.
E para que a replicação funcione,
você deve conceder permissões IAM adequadas
ao serviço S3 para que ele tenha permissão
para ler e gravar nos buckets especificados.
Portanto, os casos de uso da replicação são muitos.
A primeira é que, se você usar a replicação entre regiões, isso
pode ser útil para fins de conformidade
ou para fornecer acesso de menor latência aos seus
dados porque eles estão em outra
região, ou para replicar dados entre contas.
Para SRR, ou replicação na mesma região, isso pode ser
muito útil para agregar logs em vários S3 Buckets
ou para executar uma replicação
em tempo real entre uma conta de produção
e uma conta de teste, para que você tenha seu
próprio ambiente de teste.
Ok, então é isso sobre replicação.
Eu o verei na próxima palestra para praticar um pouco.
