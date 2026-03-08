Olá, bem-vindo a esta
sobre Docker, ECS e EKS.
Então, o que é o Docker?
O Docker é uma plataforma de desenvolvimento de software para implantar aplicativos.
A ideia é que se trata de uma tecnologia de contêineres.
Portanto, os aplicativos serão empacotados em contêineres
e esses contêineres são padronizados.
Assim, eles podem ser executados em qualquer sistema operacional.
Isso significa que seus aplicativos, uma vez em contêineres,
são executados da mesma forma, independentemente de onde forem executados.
Pode ser qualquer máquina.
Você não tem nenhum problema de compatibilidade.
O comportamento é previsível, o que significa que você tem
menos trabalho a fazer.
É mais fácil de manter e implantar e deve
funcionar com qualquer tipo de linguagem, qualquer
sistema operacional e qualquer tecnologia.
Portanto, os casos de uso do Docker são uma arquitetura de microsserviço.
Portanto, essa é uma boa palavra-chave para se ter em mente.
Transfira aplicativos do local para a nuvem.
E sempre que quiser executar um contêiner, na verdade.
Então, como o Docker funciona em um sistema operacional?
Bem, temos um servidor e, no
nosso caso, pode ser uma instância EC2, mas
pode ser qualquer
tipo de servidor e você executará um agente do Docker.
E, a partir daí, você pode iniciar os contêineres do Docker.
Portanto, seu primeiro contêiner do Docker pode
conter um aplicativo Java.
E o seu segundo contêiner do Docker pode conter um aplicativo
node JS e contêineres do Docker que podem ser executados várias
vezes da mesma forma.
Portanto, você pode ter vários contêineres
do Docker do mesmo aplicativo Java ou vários contêineres do
Docker do mesmo aplicativo node JS.
Você também pode executar bancos de dados no Docker, por
exemplo, My SQL e assim por diante.
Portanto, o Docker é muito versátil.
E, do ponto de vista do servidor,
todas essas coisas são contêineres do Docker.
Então, onde você armazena as imagens do Docker?
Bem, você os armazena
em algo chamado Docker Repository.
Ok, temos várias opções.
O primeiro é o Docker Hub, que é um repositório
público no qual você pode encontrar imagens básicas
para muitas tecnologias ou sistemas operacionais, como
Ubuntu, MySQL e assim por diante.
É muito popular.
E, para uma integração mais privada, você
tem o Amazon ECR, Amazon Elastic Container Registry, e pode
executar suas imagens privadas
nele, mas também há uma opção de repositório público
disponível no ECR chamada Amazon ECR Public Gallery.
Qual é a diferença entre o Docker e uma máquina virtual?
Bem, o Docker é uma espécie de tecnologia de virtualização, mas não exatamente
- os puristas tentarão
me bater se eu disser isso -, de modo que os recursos
são compartilhados com um host.
Isso significa que você pode compartilhar vários contêineres em um servidor.
Portanto, se
você observar a arquitetura de uma VM, terá a infraestrutura, o
sistema operacional host, o
hipervisor e os aplicativos
e o sistema operacional guest.
E é assim que, por exemplo, o EC2 funciona, por exemplo,
quando você obtém uma máquina EC2, ela é, na verdade,
uma máquina virtual executada em um hipervisor.
Assim, isso permite que a Amazon ofereça muitas instâncias de EC2 a muitos
tipos diferentes de clientes, e todas
essas instâncias de EC2, todas
essas máquinas virtuais, serão separadas.
Eles não compartilharão recursos
e serão isolados, mas, para um contêiner do Docker, você ainda tem a infraestrutura
e o sistema operacional do host, que pode ser,
desta vez, uma instância do EC2, e então
você tem o Docker Daemon e,
além disso, pode ter vários contêineres
que podem ser leves executados sobre o Docker
Daemon.
E isso permite que os contêineres realmente
convivam juntos.
Na verdade, eles podem compartilhar a rede, compartilhar
alguns dados e assim por diante.
Portanto, é um pouco menos seguro
do que uma máquina virtual, mas permite
que você execute mais contêineres em um único servidor.
E é por isso que gostamos muito dos contêineres do Docker.
Então, como você começa a usar o Docker?
Bem, primeiro você precisa escrever um arquivo Docker,
que define a aparência do seu contêiner Docker.
Portanto, temos uma imagem básica do
Docker, adicionamos alguns arquivos e, em seguida, vamos criá-la.
E isso se tornará uma imagem do Docker.
E essa imagem do Docker
pode ser armazenada em um repositório do Docker,
chamado de Push, e você a envia para o Docker Hub, que é um
repositório público, ou para o ECR da Amazon, que é
a versão da Amazon dos repositórios do Docker.
Em seguida, você pode extrair essas imagens
desses repositórios e executá-las.
E quando você executa uma imagem do Docker,
ela se torna um contêiner do Docker, que executa o código que você
criou a partir da compilação do Docker.
Esse é o processo completo do Docker.
Então, como fazer o gerenciamento de contêineres do Docker no AWS?
Bem, o primeiro é chamado de Amazon ECS.
É o Amazon Elastic Container Service.
É a própria plataforma da Amazon para gerenciamento do Docker.
Vamos dar uma olhada nisso em detalhes.
Depois, temos o Amazon EKS, que é o Amazon
Elastic Kubernetes Service, que é a versão gerenciada
do Kubernetes da Amazon, que é um projeto
de código aberto.
Vamos dar uma olhada rápida nisso.
Temos o AWS Fargate, que é a própria
plataforma de contêineres sem servidor da Amazon.
E o Fargate funciona tanto com o ECS quanto com o EKS, e faremos
um mergulho profundo no Fargate nesta seção.
Além disso, temos o Amazon ECR usado para armazenar imagens de contêineres,
como mostrei anteriormente.
Portanto, temos uma visão geral de como usar o
Docker, o que é o Docker e como usar o Docker no AWS.
Agora vamos nos aprofundar no Amazon ECS e no restante.
