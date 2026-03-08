rápida introdução ao CloudFormation e dar uma visão
geral que realmente permita que você entenda
como ele funciona.
Então, vamos criar uma pilha e, antes
de mais nada, vamos nos certificar de que estamos na região Leste dos EUA, Virgínia
do Norte, Leste dos EUA 1, porque o modelo que
criei para você só funciona nessa região.
E eu lhe direi por que quando virmos o modelo.
Portanto, certifique-se de mudar a região para esta.
Em seguida, criamos uma pilha e precisamos preparar modelos.
Portanto, há várias opções.
Podemos escolher um modelo existente,
usar um modelo de amostra e algumas amostras são fornecidas ou criar a partir
do Application Composer.
Mas vamos escolher um modelo existente.
Vamos fazer upload de um arquivo de modelo
e vou mostrar a você como é o arquivo.
Portanto, no código do seu curso em CloudFormation,
você tem 0-just-EC2. yaml.
Este é um arquivo muito simples que
tem um blog de recursos e cria uma instância chamada
My instance.
O tipo é instância EC2 e, em seguida, você tem
algumas propriedades.
A primeira é a zona de disponibilidade,
que é US East 1a, e é por isso que você
precisa escolher US East 1 como sua região no serviço
CloudFormation neste momento.
E a ID da imagem é essa ID AMI.
E, como você deve saber,
as IDs de AMI têm escopo dentro da região.
Portanto, por esses dois motivos, você deve estar no Leste 1 dos
EUA para esse hands-on.
O tipo de instância é T2 micro.
Assim, como você pode ver, definimos como
iniciar uma instância do EC2 por meio desse arquivo YAML.
Então, vamos em frente e fazer o upload desse arquivo.
Portanto, selecione-o e, em seguida, você poderá visualizá-lo
no Application Composer.
Portanto, abra isso em uma nova guia.
Portanto, aqui está meu modelo.
Portanto, como você pode ver, o Application Composer
nos dá uma compreensão visual dos nossos modelos.
Portanto, se procurarmos nos modelos,
receberemos de volta o código que acabamos de carregar bem
aqui e poderemos alterá-lo para YAML e JSON, se quisermos.
Mas, na tela, vemos que temos um componente
padrão, que é uma instância
do EC2 na minha instância.
Você pode clicar duas vezes
nela e ver o fato de que é uma instância EC2 também.
Portanto, o Application Composer é uma
boa maneira de obter um feedback visual dos seus modelos.
Enfim, voltemos à nossa pilha.
Vamos clicar em next.
Temos que fornecer um nome de pilha de demonstração.
Portanto, chamarei essa demonstração de CloudFormation e, em seguida,
alguns parâmetros.
Mas como não definimos nenhum parâmetro
em nossos modelos até o momento, não fazemos nada aqui.
Vamos clicar em next (próximo) e aqui temos as tags.
Portanto, vou mostrar a tag sendo CFDemo apenas para
mostrar como as tags funcionam no CloudFormation.
Rolamos para baixo, sem permissões para definir.
Não tocamos nessas opções e em nenhuma delas.
Então, vamos clicar em next e revisar e criar.
E quando estiver tudo pronto, clique em enviar.
Portanto, como você pode ver agora, esse modelo que carreguei
vai gerar alguns eventos e isso foi muito rápido.
Portanto, os eventos estão
concluídos e isso realmente criou um recurso bem aqui, que é uma instância
do EC2.
Portanto, o código obteve um recurso com isso, e é por isso que
ele é chamado de Infraestrutura como código.
Portanto, você pode clicar nessa instância do EC2.
Como você pode ver agora mesmo no console do EC2,
minha instância está em execução
e você pode verificar o fato de que, de fato, ela é uma instância
do tipo T2 micro.
E você também pode
verificar se a ID AMI que selecionamos é a que
foi inserida em nosso modelo.
Portanto, tudo isso é muito conveniente.
Além disso, notamos que, se você acessar nossa instância
do EC2 e observar as tags, veremos
que algumas tags foram aplicadas pelo CloudFormation,
que são o nome do CloudFormation, o nome do ID
lógico e o ID da pilha, mas também o nome que
especificamos.
Assim, a tag que especificamos com o nome CFDemo
também foi aplicada a essa instância do
EC2 e, portanto, foi nomeada corretamente.
Agora que temos uma instância,
vamos atualizar essa pilha.
Então, clicamos em atualizar
e substituímos o modelo existente.
E, desta vez, vamos
escolher o arquivo 1-ec2-with-sg-eip.
E se você der uma olhada nele, esse arquivo está bem aqui.
Portanto, agora temos um arquivo mais completo.
Temos uma seção de parâmetros
para definir a descrição do grupo de segurança.
Temos a seção de instância do EC2, que
é um pouco mais completa,
pois agora ela tem grupos de segurança e tem dois deles.
Temos um Elastic IP aqui que está anexado à minha instância.
E temos um grupo de segurança aqui definido para regras de SSH.
Portanto, a porta 22 estará
aberta e temos o grupo de segurança do
servidor, que estará aberto na porta 80 para todos
e na porta 22 para um IP muito específico.
Portanto, este é um modelo mais completo do CloudFormation.
Agora vamos voltar ao CloudFormation
e aplicar esses modelos.
Portanto, aqui somos solicitados com um parâmetro.
Então, qual é a descrição do grupo de segurança?
Então, vamos inserir a descrição da demonstração.
E, como você pode ver agora, estamos inserindo alguns
textos, o que fará com que tudo varie.
Não tocamos nas etiquetas, não tocamos em nada.
Vamos clicar em next.
E agora, como estamos aplicando uma atualização,
como você pode ver, temos um conjunto de alterações.
Assim, podemos visualizar os
conjuntos de alterações, que é o que será alterado
em nossa pilha do CloudFormation.
Portanto, como você pode ver, algumas coisas foram adicionadas.
Há um Elastic IP, um grupo de segurança SSH e um grupo de segurança
de servidor.
E ele é adicionado, portanto é novo.
E minha instância será alterada,
será modificada, e há uma coluna aqui que diz replacement
true.
Isso significa que essa instância do EC2 será substituída,
ou seja, a instância anterior será excluída e uma
nova será criada.
Portanto, é bom saber caso você tenha alguns
dados em sua instância do EC2.
Então, agora vamos enviar essa atualização e ver o que acontece.
Portanto, o CloudFormation é um serviço muito
inteligente porque, bem, a partir deste código, ele é capaz de descobrir
exatamente o que fazer graças aos conjuntos
de alterações, de modo que sabe
exatamente o que criar primeiro.
Portanto, como você pode ver, o grupo de segurança do
servidor e o grupo de segurança SSH já foram criados.
E só então ele atualizará a instância do EC2.
Portanto, agora a minha instância é uma atualização em andamento e, como você
pode ver, ela diz que as atualizações solicitadas
exigem a criação de um novo recurso físico, portanto, a criação de um.
Portanto, se entrarmos no
console do EC2 e removermos esse filtro,
veremos que temos duas instâncias do EC2.
Este foi criado antes e este é o novo, estava
pendente e agora está em execução.
Portanto, uma nova instância foi criada e, uma
vez criada, ela será atualizada aqui, a atualização
está concluída.
E agora temos o MyEIP.
Portanto, agora o Elastic IP será criado e anexado
à minha instância do EC2.
Portanto, se formos rápidos e acessarmos
o Elastic IP no lado esquerdo, mesmo que não tenhamos visto
o que é, aqui está o Elastic IP que foi criado corretamente,
marcado corretamente e já está anexado à nossa instância
do EC2.
Portanto, se eu clicar neste e depois
em rede na parte inferior, você verá que o endereço
Elastic IP aqui foi anexado.
Portanto, tudo foi feito pelo CloudFormation e foi bem feito.
E se você olhar para o CloudFormation agora
nos eventos, como pode ver, o Elastic IP foi
criado e, em seguida, houve uma limpeza em andamento.
Isso significa que a instância anterior
do EC2 aqui foi encerrada, o que é muito
útil porque o CloudFormation
cuida de tudo.
Assim, você pode acessar a guia
de recursos e ver tudo o que foi criado por meio do CloudFormation.
Além disso, se você acessar o modelo
e clicar em visualizar no Application Composer,
poderá ver agora sua nova arquitetura.
Portanto, temos uma instância do EC2 conectada a um Elastic IP
e conectada a dois grupos de segurança.
Isso é muito útil,
pois permite obter novamente uma
representação visual dos nossos modelos.
Então, finalmente, é claro, a confirmação.
Você pode excluir as coisas manualmente.
Você pode excluir esse Elastic IP e assim por diante,
e as instâncias do EC2 manualmente.
Mas, na verdade, isso não é recomendado.
Você não quer tocar em nada manualmente ao
usar o CloudFormation.
Em vez disso, você deseja atualizar os modelos
ou, se quiser excluir tudo, basta clicar em excluir.
E o CloudFormation excluirá todos os recursos da pilha.
E os recursos da pilha também serão excluídos nas ordens
corretas.
Assim, o CloudFormation descobrirá o que deve ser excluído
primeiro e assim por diante para limpar tudo.
Portanto, o CloudFormation é um serviço realmente poderoso para
fazer infraestrutura como código porque é declarativo.
Basta dizer o que você quer e
o CloudFormation descobre, e todo o código controlará
sua infraestrutura, o que é muito, muito útil.
Portanto, aprender a usá-lo e a escrevê-lo
pode ser uma habilidade muito boa na AWS.
Espero que tenham gostado
e nos veremos na próxima palestra.
