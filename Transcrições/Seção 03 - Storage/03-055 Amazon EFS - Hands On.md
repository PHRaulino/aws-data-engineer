Então, vamos praticar
Então, vamos criar nosso sistema de arquivos
e aqui podemos dar a ele um nome opcional,
mas vou deixá-lo vazio, e temos que escolher
uma VPC onde queremos nos conectar ao nosso sistema de arquivos.
Portanto, vamos deixá-la como a VPC padrão também, e podemos simplesmente
clicar em criar e pronto.
Mas quero lhe mostrar as opções.
Então, vamos clicar em Personalizar.
Portanto, aqui novamente, deixaremos o nome vazio e opcional.
Em seguida, precisamos escolher um tipo de sistema de arquivos.
Portanto, temos duas opções.
Temos o regional, que oferece um sistema de arquivos dentro
da região em várias zonas de disponibilidade, o que proporciona
uma disponibilidade e durabilidade
muito altas dos dados.
Mas se você precisar reduzir os custos, poderá
usar a opção de uma zona, caso em que deverá
escolher uma zona de disponibilidade específica.
E isso é bom para ambientes de desenvolvimento, mas não
é bom para ambientes de produção,
pois se essa zona de disponibilidade ficar indisponível, seus
dados ficarão inacessíveis.
Portanto, definitivamente, você deve usar a regional nas
configurações de produção e, neste momento, usaremos
a regional para esta prática.
Em seguida, podemos ativar ou desativar os backups automáticos,
mas é recomendável mantê-los ativados.
Em seguida, temos o gerenciamento do ciclo de vida.
Portanto, isso serve para mover os dados
entre diferentes níveis de armazenamento para economizar custos.
Portanto, é possível fazer a transição
para acesso pouco frequente ou arquivamento e, em seguida, voltar ao padrão.
Portanto, estamos dizendo que, se um arquivo não tiver sido acessado
por 30 dias, mas você pode obviamente personalizar isso, se um
arquivo não tiver sido acessado por 30 dias, mova-o para a camada de armazenamento
de acesso pouco frequente e ele será mais barato
para você, exceto quando
você acessar o arquivo.
Mas a probabilidade
é que, após 30 dias, você raramente acesse o arquivo.
E, se o arquivo não tiver sido acessado, por exemplo,
em 90 dias desde o último acesso, ele será
movido para o arquivo, que será ainda mais barato como classe
de armazenamento.
E, por exemplo, você diz que aqui,
quando o arquivo é acessado pela primeira vez,
no primeiro acesso, a transição volta para o padrão
porque, por exemplo, presumimos que ele será
reutilizado muito mais vezes.
Portanto, isso é chamado de gerenciamento do ciclo de vida.
Portanto, podemos manter essa criptografia como está.
Deixamos tudo ativado, isso é perfeito.
E depois temos as configurações de desempenho.
Portanto, para as configurações de desempenho, temos o modo de taxa de transferência
e você deve ter três opções.
Portanto, o aprimorado é apenas uma categoria
para reagrupar, elástico e provisões.
Portanto, você tem o modo de taxa de transferência elástica,
o modo de taxa de transferência provisionada e o modo de
taxa de transferência intermitente.
Então, vamos começar com o estouro.
Portanto, o bursting é uma forma de escalonar a taxa de transferência de acordo com a quantidade
de armazenamento que você está realmente usando
e ultrapassando um pouco o limite, por
isso é chamado de bursting.
Portanto, se você tiver um gigabyte,
obterá uma taxa de transferência baseada em um gigabyte.
Se você tiver um terabyte, terá uma taxa de transferência
maior porque usará mais armazenamento.
Depois, havia o modo avançado.
E agora a elasticidade é recomendada, o que significa:
"Ei, independentemente do tamanho do seu sistema de arquivos EFS, forneceremos
toda a E/S de que você precisa, escalonaremos
automaticamente e você
pagará apenas pelo que usar".
Portanto, isso é melhor quando você tem uma
carga de trabalho com E/S imprevisível onde, por exemplo, você pode
escalar de zero megabytes por segundo para
cem megabytes por segundo em pouco tempo.
É por isso que esse é o modo recomendado,
pois não exige que você pense em
nenhuma configuração.
E o último, então, temos o elástico estourado,
e o último é provisionado.
Isso ocorre quando você sabe
com antecedência a taxa de transferência de que precisará.
Portanto, esse é o modo de provisão.
Então você diz: "Ei,
com certeza vou precisar de 100 megabytes por segundo".
Além disso, você também tem um limite de explosão
de 300 megabytes por segundo.
E como você provisiona o throughput
com antecedência, você pagará por ele com antecedência.
Portanto, elástico é a configuração recomendada.
E, se você observar as configurações adicionais,
verá que temos a finalidade geral e a E/S máxima.
Portanto, no caso da elasticidade, você obtém a E/S necessária com base
no desempenho de que precisa.
Portanto, a finalidade geral é a única opção para o modo de desempenho, mas se
você usar bursting ou provisões, terá a opção de escolher
entre duas configurações.
Portanto, de uso geral, que oferece aplicativos de alto
desempenho e sensíveis à latência.
Isso significa que a latência é muito baixa,
mas se você quiser obter o máximo de modo de E/S,
isso é para cargas de trabalho altamente paralisadas e você pode tolerar
uma latência mais alta.
Portanto, à custa de uma latência mais alta,
você também obtém mais E/S.
Isso é bom em um tipo de configuração de big data,
mas a melhor configuração recomendada agora
para a AWS é usar aprimorado com finalidade geral e elástico.
Está bem? Então é isso para as opções.
Espero que não seja muito confuso.
Não gosto do fato de que, no enhanced, há elasticidade e
provisão, mas na verdade temos apenas três opções.
Temos bursting, elastic e provision, e é disso
que você deve se lembrar para o exame.
Certo, vamos clicar em Next agora.
Em seguida, temos as configurações de acesso à rede, que são muito
importantes, e precisamos escolher uma VPC.
Escolherei a VPC padrão e, em seguida, os alvos de montagem.
E como escolhemos um tipo regional
de sistema de arquivos EFS, temos o AZ gratuito à nossa disposição.
Portanto, cada AZ será atribuído a uma sub-rede.
Vou deixar como está, que são as sub-redes padrão.
O IP é automático e precisamos atribuir um grupo de segurança.
Portanto, precisamos
criar um grupo de segurança específico para o meu sistema de arquivos EFS.
Então, vou para o console do EC2 e depois vou para
os Grupos de segurança.
Criarei um grupo de segurança
e o chamarei de sg-efs-demo.
E eu o chamarei de EFS Demo SG.
Por enquanto, não teremos nenhuma regra de entrada.
Vou clicar em Criar grupo de segurança e não podemos ter isso.
Portanto, a demonstração do EFS é boa o suficiente.
Portanto, minha demonstração do EFS foi criada com
êxito e, para que ela apareça aqui,
preciso atualizar a página.
Portanto, começaremos
tudo de novo, mas as configurações são as básicas, as
padrão que virão a seguir.
E agora posso remover esses grupos de segurança
e escolher o grupo de segurança de demonstração do
EFS que criei anteriormente.
Ok, estamos bem.
Portanto, agora já fizemos toda a configuração de acesso à rede.
Clicarei em Next.
Temos uma política de sistema de arquivos que é opcional
e não tocaremos nela neste momento.
Isso é muito avançado e não precisamos disso no momento.
Portanto, vou clicar em Next.
E aqui podemos revisar
e criar todas as configurações do sistema de arquivos.
Portanto, estamos satisfeitos com isso.
E quando terminarmos, basta clicar em Create.
Agora meu sistema de arquivos está sendo criado e entrarei
em contato com você quando ele for criado.
Meu sistema de arquivos agora está disponível e posso acessá-lo
e ver que há seis kilobytes de tamanho sendo usados
no momento.
E quando você tem um sistema de arquivos EFS, paga apenas pelo armazenamento
que usa, portanto, no momento, meu custo é zero.
Portanto, isso é bom, isso é criado.
E agora queremos montar isso em instâncias do EC2.
Portanto, você sabe que, na próxima
etapa, vamos criar instâncias do EC2.
Então, vamos lançar uma instância.
E chamarei essa instância de Instância
A, porque a lançaremos na sub-rede AZA.
Portanto, vamos executar o Amazon Linux versão 2.
Estamos prontos para ir, usaremos o t2. micro porque é elegível
para a camada gratuita.
Desabilitaremos o par de chaves.
Faremos apenas a conexão da instância EC2
para nos conectarmos à nossa instância EC2.
Para as configurações de rede, deixarei tudo como
está e haverá um novo grupo de segurança criado
com essas regras aqui.
Portanto, permite o acesso SSH de qualquer lugar, o que é bom.
Em seguida, temos oito gigabytes de armazenamento GP2.
Mas agora, como queremos configurar o armazenamento
da instância do EC2
no Amazon EFS, podemos fazer isso de dentro do console
do EC2, o que é muito interessante.
Então, vou lhe mostrar como fazer isso.
Antes, era necessário executar alguns comandos.
Portanto, há 0 x sistemas de arquivos e você edita e ele diz que não
é possível adicionar um sistema de arquivos antes
de escolher selecionar uma sub-rede.
Então, voltamos para cima, acessamos Network Settings (Configurações
de rede), Edit (Editar) e, na sub-rede, vou escolher eu-west-1a.
Portanto, agora que minha sub-rede foi criada, posso voltar aos
sistemas de arquivos.
E, como você pode ver, posso adicionar um sistema de arquivos EFS ou FSx.
Portanto, adicionaremos um sistema de arquivos
EFS e, em seguida, clicaremos em Add Shared File System.
Ele será vinculado ao meu EFS aqui mesmo.
O ponto de montagem é /mnt/efs/fs1. Isso é bom o suficiente para nós.
Isso criará e anexará automaticamente
grupos de segurança para nós, o que é incrível.
Em seguida, ele montará automaticamente
o sistema de arquivos compartilhados, anexando
os scripts de dados do usuário necessários.
Portanto, no passado, tínhamos que nos
executar manualmente na instância do EC2 ou criar nosso próprio
script de dados do usuário.
Mas agora isso é feito para nós
pelo console do EC2, o que é muito bom.
Vamos criar uma instância e iniciá-la.
Então, essa instância foi iniciada.
Posso visualizar todas as instâncias
e vou iniciar uma nova.
Ok, chamarei esta de Instância B.
Teremos o Amazon Linux 2, mais uma vez para agilizar,
vou prosseguir sem um par de chaves, vou entrar no eu-west-1b.
Posso simplesmente selecionar o grupo de segurança do launch-wizard-2
que foi criado anteriormente.
E, novamente, precisamos editar isso e adicionar
um sistema de arquivos do tipo EFS e usaremos
o mesmo sistema de arquivos de antes e os mesmos pontos
de montagem e deixaremos
essas opções ativadas também.
Portanto, estamos bem. Vamos iniciar essa instância.
E agora vamos dar uma olhada
nas coisas interessantes que aconteceram.
Por isso, vou fazer com que o estado instantâneo seja igual à execução e atualizá-lo
até que eu veja as duas instâncias.
Portanto, agora os dois estão concorrendo.
E o interessante é que, se entrarmos
no console do EFS e formos para a guia de rede,
como podemos ver agora, cada zona de disponibilidade
agora tem vários grupos de segurança.
Portanto, temos a demonstração do EFS que criamos
anteriormente, mas também o efs-sg-1 e o efs-sg-2, que foram criados automaticamente pelo
console do EC2 para nós e anexados ao nosso sistema
de arquivos EFS.
Portanto, se eu entrar em minhas instâncias do
EC2 e depois no grupo de segurança aqui, posso ver,
por exemplo, este efs-sg-2 e ver as regras de entrada.
E, como você pode ver, ele permite o protocolo NFS na porta 2049 e a origem
dele, se dermos uma olhada nas próprias
regras de entrada, a origem disso
é esse grupo de segurança e esse grupo
de segurança é o que
está anexado à minha instância do EC2, a instância B.
Isso permite que a minha instância B acesse o sistema de arquivos
EFS porque esse grupo de segurança aqui chamado efs-sg-2 está
anexado ao meu sistema de arquivos EFS.
Portanto, toda a configuração é feita pela AWS para nós, o que é realmente muito bom.
Portanto, agora, se eu entrar em uma dessas
instâncias, vamos nos conectar usando a conexão de instância
do EC2 nessa guia e, em seguida, também farei exatamente a mesma coisa
conectando-me à instância B por meio da conexão de instância do EC2.
Portanto, agora posso, por exemplo, verificar o fato de que
sim, em ls /mnt/efs/fs1/ há um sistema de arquivos EFS e agora precisamos
criar arquivos nele.
Portanto, para simplificar, elevarei
meu direito e digitarei sudo SU e,
em seguida, poderei fazer echo "hello world"
em /mnt/efs/fs1/hello. txt.
Então, criamos esse arquivo chamado hello. txt.
E se eu fizer cat e depois todo esse nome de arquivo aqui, como você
pode ver, ele diz hello world.
Portanto, esse arquivo foi criado em meu sistema de
arquivos EFS a partir dessa instância do EC2, que é um eu-west-1a.
Mas agora, se eu for para a minha segunda instância do EC2 e fizer LS e depois o
mesmo sistema de arquivos, então eu procuro por arquivos nele, como você
pode ver, também veremos esse hello. txt nele.
E se eu fizer cat e depois cat o arquivo, olá. txt, ele também diz hello
world.
Portanto, como você pode ver, o sistema de arquivos EFS está
de fato montado como uma unidade de rede em ambas as minhas instâncias do
EC2, e elas estão em AZs diferentes e compartilham
o mesmo EFS.
Isso é incrível e é um tipo diferente de armazenamento
que você teve a demonstração agora.
Então é isso para a demonstração do EFS. Isso foi bem completo.
Agora, para limpar tudo, o que você pode
fazer é encerrar essas duas instâncias do EC2.
Então, você vai até aqui e os encerra.
Outra coisa que você pode fazer é acessar
o sistema de arquivos EFS, excluí-lo inserindo o ID do sistema de
arquivos e, depois que tudo for excluído,
você poderá acessar os grupos de segurança e excluir
os grupos de segurança adicionais
que foram criados durante esta
demonstração.
Muito bem, isso é tudo para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
