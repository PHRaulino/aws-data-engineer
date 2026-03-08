Então, vamos falar
sobre a outra maneira de executar contêineres na AWS, que é usando o Amazon EKS.
Portanto, Amazon EKS significa Amazon Elastic Kubernetes Service.
Portanto, é uma maneira, como o nome
indica, de iniciar e gerenciar o cluster do Kubernetes no AWS.
Então, o que é o Kubernetes?
Bem, esse é o logotipo azul
que você vê no canto superior direito da tela.
O Kubernetes é um sistema de código aberto para implantações
automáticas, dimensionamento e gerenciamento de aplicativos
em contêineres, geralmente do Docker.
Portanto, é uma alternativa ao ECS, que tem um objetivo semelhante,
que é executar seus contêineres, mas uma API muito diferente.
Já o Kubernetes é de código aberto
e usado por muitos provedores de nuvem diferentes, o que proporciona
algum tipo de padronização.
Portanto, o EKS oferece suporte a dois modos de inicialização,
novamente o modo de inicialização do EC2, se você quiser
implantar o modo de trabalho como instâncias do EC2,
ou o modo Fargate, se quiser implantar contêineres
sem servidor em um cluster do EKS.
Portanto, o caso de uso do EKS é se sua empresa já estiver
usando o Kubernetes no local, ou já estiver
usando o Kubernetes em outra nuvem, ou se
quiser apenas usar a API do Kubernetes e quiser
usar o AWS para gerenciar o cluster do Kubernetes,
então ela usaria o Amazon EKS.
Então, novamente, o Kubernetes, de uma perspectiva de exame,
é agnóstico em relação à nuvem, pode ser usado em qualquer nuvem,
como Azure, Google Cloud e assim por diante.
Isso significa que, se você estiver
tentando migrar entre nuvens ou contêineres,
usar o Amazon EKS pode ser uma solução muito mais simples.
Portanto, em termos de diagrama, é assim que ele se parece.
Portanto, temos um VPC, 3 AZ separados em sub-redes
públicas e sub-redes privadas.
Assim, você criaria nós de trabalho do EKS,
que seriam instâncias do EC2, por exemplo,
e cada um desses nós executaria pods do EKS.
Portanto, eles são muito parecidos com as tarefas
do ECS, mas, do ponto de vista da nomenclatura,
sempre que você vir pods, isso está relacionado ao Amazon Kubernetes, certo?
Portanto, temos pods do EKS e eles estão sendo executados em nós do EKS, e esses nós podem ser
gerenciados por um grupo de dimensionamento automático.
Agora, de forma muito semelhante ao ECS, se
você quisesse expor o EKS Service e o Kubernetes Service, poderíamos
configurar um balanceador de carga privado ou um balanceador
de carga público para se comunicar com a Web.
Portanto, vamos resumir os diferentes
tipos de nós existentes no Amazon EKS.
Portanto, você tem o Manage Node
Groups, e é o AWS que criará e gerenciará os nós, ou
seja, as instâncias do EC2 para você.
E esses nós fazem parte de um grupo Auto Scaling,
gerenciado pelo próprio serviço EKS.
E você tem suporte para instâncias On-Demand e Spot.
Se desejar, você também pode
optar por autogerenciar os nós, caso queira ter mais
personalizações e mais controle.
Portanto, nesse caso, você mesmo precisa criar
os nós e, em seguida, registrá-los em um cluster EKS e gerenciar
seus próprios nós como parte de um ASG.
Você ainda pode usar a AMI otimizada do Amazon EKS pré-criada para isso,
o que economiza um pouco de tempo,
ou pode criar sua própria AMI, o que é mais complicado.
Isso também é compatível com as instâncias On-Demand e Spot.
E, por fim, se você não quiser ver nenhum nó,
o Amazon EKS, como eu disse, é compatível com o modo Fargate, no
qual não há necessidade de manutenção
e nenhum nó é gerenciado, você pode simplesmente executar contêineres
sobre o Amazon EKS.
Agora você pode anexar volumes de dados ao seu cluster do Amazon EKS.
Para isso, você precisa especificar um manifesto StorageClass
em seu cluster EKS, e isso aproveita algo chamado
Container Storage Interface, driver compatível com CSI.
Portanto, palavras-chave a serem observadas no exame.
E você tem suporte para o Amazon EBS, você
tem suporte para o Amazon EFS, e esse é o único tipo
de classe de armazenamento que funciona com o Fargate.
Você tem o Amazon FSx para
Lustre e o Amazon FSx para NetApp ONTAP.
Então é isso para o Amazon EKS.
Espero que tenham gostado e nos veremos na próxima palestra.
