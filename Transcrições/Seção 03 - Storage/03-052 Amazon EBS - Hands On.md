Então, vamos
dar uma olhada nos volumes EBS anexados à nossa instância.
e depois for para a guia de armazenamento, verá
que há um dispositivo raiz e um dispositivo de bloqueio
nele.
Como você pode ver, temos um volume
de oito gigabytes atualmente conectado
à nossa instância do EC2.
Então, o que posso fazer é clicar nesse
volume e ele me levará à interface de volumes do AWS.
E podemos ver que, sim,
de fato, nosso volume existe e está lá.
Ele está em uso como mostrado aqui e está anexado
a uma instância bem aqui.
Portanto, temos um tipo diferente de console aqui e, para
acessá-lo, basta ir para o lado esquerdo
e clicar em volumes.
Portanto, como podemos ver, agora temos um EBS de oito gigabytes
e o que posso fazer é criar um segundo volume.
Então, deixe-me criar um volume
e terei muitas opções para escolher,
GP2, GP3 e assim por diante,
mas usarei apenas o GP2 do tipo de tamanho de dois gigabytes.
E, em seguida, para a zona de disponibilidade,
posso escolher a mesma onde está minha instância do EC2.
Portanto, para isso, vou acessar minha instância do EC2, aqui, e descobrirei
em qual zona de disponibilidade ela está.
Então, eu rolo a tela
para baixo e ele estará na rede.
Então, rolei a tela para baixo na rede
e aqui, na zona de disponibilidade, está escrito eu-west-1b.
Portanto, o volume que criarei estará
em eu-west-1b porque os volumes do EBS
estão vinculados a uma AZ específica.
Então, isso é bom.
Vou fazer isso e criar esse volume.
E agora meu volume foi criado.
E o que posso fazer é clicar nele, pois
este não está anexado no momento.
Ok, ele está sendo criado, então
vou atualizá-lo para ver se ele foi criado.
Ok, ele está disponível e ainda não está anexado.
Portanto, como ele está
disponível, o que posso fazer
é agir e anexar o volume, e precisamos encontrar
uma instância.
Portanto, temos um em execução bem aqui.
Então, vamos anexar esse volume à minha instância,
clicar em anexar volume e pronto, nossa instância
agora tem dois volumes EBS anexados a ela.
Como podemos saber?
Bem, posso atualizar esta página,
acessar o armazenamento no meu console do EC2 e rolar para baixo.
Como você pode ver agora nos dispositivos de bloco,
tenho dois dispositivos de bloco.
Tenho o de oito gigabytes
e o de dois gigabytes.
Para usar de fato esse novo dispositivo de bloco,
é um pouco mais complicado
e está fora do escopo deste curso,
mas você pode ir para formatar o volume do EBS, anexar o EC2 e deve encontrar algo como "sim,
disponibilizar um volume do Amazon EBS para uso no Linux"
e isso lhe dá instruções sobre como fazer isso, mas, novamente, está fora do escopo deste
curso.
Portanto, agora, se eu entrar em meus volumes
e criar um volume, poderei criar um volume de dois
gigabytes de GP2, mas desta vez o AZ será eu-west-1a e não
eu-west-1b.
Portanto, será um AZ diferente
daquele da minha instância do EC2.
E a razão pela qual faço isso é para mostrar
a vocês que, no momento, temos três volumes de GP2.
Então, deixe-me atualizar isso.
Portanto, o último está disponível e é um AZ diferente,
portanto, eu-west-1a.
E se eu fizer ações e depois anexar o volume, como você pode
ver, não poderei anexá-lo à minha instância do EC2 porque
minha instância do EC2 está em eu-west-1b.
Portanto, podemos ver que os volumes do EBS estão
de fato vinculados a uma zona de disponibilidade específica.
Por fim, o que posso fazer é pegar esse volume,
executar uma ação, excluir o volume e ele desaparecerá.
E isso realmente mostra o poder da nuvem.
Posso simplesmente solicitar volumes
e excluir volumes em questão de segundos.
Temos dois volumes do EBS aqui e quero mostrar a você
um comportamento interessante.
Então, o que acontece se eu encerrar minha instância?
Lembre-se, e vou lhe mostrar novamente,
que esse volume raiz de oito gigabytes tem
o atributo delete on termination.
Então, como podemos saber?
Bem, se eu for para o meu armazenamento
e, em seguida, para os meus dispositivos de bloco, para esta
tabela aqui, e rolar até a direita, você verá
que o primeiro tem a opção de excluir na terminação sim
e o segundo não.
Então, por que esse é sim?
Bem, não sei se você
se lembra, mas quando você passa pelo processo
de iniciar uma instância, certo?
Em seguida, role para baixo até o armazenamento e, aqui, se você clicar em avançado,
poderá ver o fato de que são suas raízes de oito gigabytes
e, por padrão, esse atributo de exclusão
no encerramento é sim, o que faz sentido, mas você pode defini-lo
como não se quiser manter a raiz
depois de encerrar a instância.
Isso explica por que estamos vendo
o "sim" nessa tabela.
Portanto, se eu for em frente e encerrar minha instância, o que farei,
ela dirá que foi encerrada com sucesso e, portanto,
será realmente removida daqui.
Posso voltar aos meus volumes do EBS.
Posso atualizá-los.
E o que vai acontecer é que, em
breve, ele estará disponível, pois
será desvinculado da minha instância do EC2 e,
em seguida, será encerrado.
Portanto, vou fazer uma pausa até que isso seja feito.
E aqui vamos nós.
Portanto, meu volume de oito gigabytes desapareceu.
Só resta o meu volume de dois gigabytes
e, se eu for ao console do
EC2, bem, ele diz que minha primeira instância foi encerrada.
Então é isso para esta palestra.
Espero que tenham gostado
e nos veremos na próxima palestra.
