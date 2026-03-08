Então, no console do DynamoDB,
no lado esquerdo, você tem o DAX.
E o DAX não faz parte da camada gratuita, portanto,
a criação de um cluster DAX não será gratuita, mas você pode
ir em frente e ver o processo.
Então, você cria um cluster, por exemplo, DemoDAX e, em
seguida, a família de nós,
seu cluster DAX.
Pode ser do tipo t ou do tipo r.
Então, r é memória e t é para bursting, portanto,
isso é recomendado para casos de
uso relacionados a uma taxa
de transferência menor, e isso é para capacidade sempre pronta, certo?
Ou podemos comparar todas as famílias e, aqui,
você pode selecionar os tipos de nós que deseja.
Então você quer um r5. grande e eu tenho o r5. 4xlarge e assim por diante ou
você gostaria de ter um t2. pequeno e assim por diante.
Portanto, neste exemplo, usarei um t2. pequeno e, em seguida,
o tamanho do cluster.
Então, você quer de 1 a 11 nós, para que eles continuem
aumentando a capacidade.
Três lhe darão uma configuração de vários AZs, certo,
mas um será bom, por exemplo, para apenas um AZ
ou para desenvolvimento.
Mas se você tiver um ou dois nós,
poderá ter uma disponibilidade reduzida, certo?
Então, vamos seguir em frente com um nó.
Vou criar isso para você, mas você não precisa ir
em frente porque isso lhe
custará algum dinheiro.
Agora, o grupo de sub-rede é: a qual
grupo de sub-rede você deseja associá-lo?
Portanto, o demosubnetgroup deve
estar dentro de um grupo de sub-rede específico e em uma VPC,
portanto, você escolhe o ID da VPC e, em seguida,
as sub-redes que deseja ter.
Obviamente, três sub-redes significam que você pode ter
três nós e estar em uma configuração altamente disponível.
Controle de acesso, então o que é um
grupo de segurança para
acessar seu cluster DAX e você precisa abrir a porta 8111, ok,
ou 9111 se fizer a criptografia em trânsito.
Portanto, precisamos ir em frente e criar um grupo de segurança
no console do EC2.
Mas, neste momento, vou manter a simplicidade
e usar apenas o grupo de segurança padrão,
apenas para mostrar o processo.
E, em seguida, a alocação
de AZ, você quer ter uma alocação automática
ou distribuir seus nós manualmente?
Portanto, vamos mantê-lo como automático.
Em seguida, para as permissões
do IAM, você precisa fornecer uma função
de serviço do IAM que dará ao cluster DAX acesso ao DynamoDB.
Portanto, vamos apenas criar
essa função IAM chamada DAXtoDynamoDB, e a política
será criada.
Forneceremos direitos de leitura/gravação
e daremos acesso a todas as tabelas, mas obviamente
poderíamos limitar algumas tabelas, se necessário.
Em seguida, criptografaremos os dados em trânsito
e em repouso em nosso cluster
DAX, o que é bom.
E, em seguida, para os grupos de
parâmetros, escolheremos o existente, ou seja, este.
E poderíamos, no lado esquerdo, definir
mais alguns parâmetros, graças aos grupos de parâmetros.
Portanto, isso basicamente informará por quanto tempo
os itens devem ser armazenados em cache, graças ao tempo de vida, e também qual
é o tempo de vida da consulta.
Portanto, essas são as configurações que você
tem como parte do grupo de parâmetros.
Mas, por padrão, o 1. 0 está lhe dando cinco minutos
de TTL no tempo do item e no tempo de consulta.
Ok, a janela de manutenção, portanto, obviamente,
o DAX será ocasionalmente corrigido e atualizado, e é por isso
que é bom ter uma configuração
do tipo multi AZ.
Assim, você pode dizer que não
tem preferência ou especificar seu período de tempo, suas
tags, e pronto.
Você pode revisá-lo e criar seu cluster.
Portanto, meu cluster DAX foi criado e vamos
dar uma olhada.
Portanto, o mais importante que
quero que você observe é que aqui há um endpoint de cluster,
e esse é o endpoint que seu aplicativo deve aproveitar
para aproveitar o recurso DAX.
Agora, podemos dar uma olhada nos
nós, para que possamos
ver os tipos de nós, quantas vCPUs por nó, memória e assim por diante.
Portanto, podemos adicionar nós ao longo do tempo se
quisermos, mas, como podemos
ver, não podemos alterar os tipos de nós, certo?
E precisamos criar um novo cluster DAX, se você quiser.
Podemos ter algum
monitoramento, portanto, podemos fazer
alarmes e métricas para saber se o cache está sendo usado
corretamente ou não, ou seja, acertos e erros de cache para itens e consultas,
utilização da CPU e assim por diante.
Portanto, isso é muito, muito
útil para ver se o DAX é eficaz para você.
Events (Eventos), para monitorar os eventos do seu banco de dados,
bem como as configurações, caso queira modificar algumas configurações,
como um grupo de parâmetros, configuração de rede, configuração
de segurança, janela de manutenção e tags, certo?
Então é isso para o DAX.
Espero que você tenha gostado.
Agora vou excluir esse cluster, incluindo
todos os alarmes do CloudWatch, e nos veremos
na próxima palestra.
