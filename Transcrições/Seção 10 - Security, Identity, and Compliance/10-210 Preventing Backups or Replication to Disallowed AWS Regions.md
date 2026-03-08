fora de áreas geográficas onde você
não tem permissão para tê-los.
Portanto, muitas vezes você terá restrições quanto ao local onde os
dados podem ser armazenados.
Países diferentes têm leis diferentes sobre como as informações
de identificação pessoal são armazenadas, leis de privacidade e coisas do gênero.
Portanto, às vezes é preciso ter cuidado com
a jurisdição em que os dados estão sendo armazenados.
E é muito fácil enviar dados por engano ou acidentalmente
para algum lugar onde eles não deveriam estar.
Uma causa muito comum disso são os backups ou a replicação,
em que talvez você esteja sendo muito bem-intencionado e fazendo
o backup dos dados em uma região diferente para melhorar a resiliência
em caso de falhas em uma região.
Mas, se não tomar cuidado, você pode acabar
fazendo esse backup ou essa replicação em um local
onde os dados não podem residir.
Portanto, há algumas maneiras de impor isso.
Há um sistema chamado AWS Organizations, sobre o
qual não falamos muito, mas ele existe
e tem algo chamado políticas
de controle de serviço.
Essa é uma maneira de aplicar esses tipos de
restrições geográficas.
A maneira mais comum seria usar apenas as políticas de IAM e as políticas
de bucket do S3 para garantir que você esteja
bloqueando tudo na região em que os
dados têm permissão para estar.
Portanto, é preciso refletir mais sobre suas políticas de IAM e pensar
não apenas em quais operações estou permitindo, mas onde estou
permitindo que essas coisas aconteçam.
Portanto, é preciso ter muito cuidado,
especialmente quando estiver configurando as permissões
para backups e replicação para RDS, Aurora Redshift ou qualquer outro banco de
dados ou armazenamento de dados.
Além disso, você quer configurar seus monitores
e alarmes com o CloudTrail e o CloudWatch.
Portanto, se algo for enviado por engano para o país errado, pelo
menos você saberá rapidamente
e poderá resolver a situação.
Apenas como um exemplo real, aqui está uma política
de IAM e seu objetivo é garantir
que não faremos nenhum backup de RDS fora das
regiões Leste dos EUA e Oeste dos EUA.
Portanto, se você estudar essa declaração
aqui, estaremos dizendo que só permitiremos criar
snapshot de BD e criar cópia de snapshot de BD para as regiões US West one e
US East one.
Portanto, isso está restringindo esses backups a apenas
essas duas regiões.
No entanto, permitiremos que todo o
resto aconteça em qualquer lugar.
Portanto, a segunda parte
dessa política diz que permitiremos qualquer outra ação
que não seja criar um snapshot de BD ou copiar um snapshot de BD em qualquer lugar.
Portanto, isso é apenas para garantir
que não estamos replicando dados em algum lugar fora
dessas regiões, mas ainda podemos acessar esses
dados de qualquer lugar.
