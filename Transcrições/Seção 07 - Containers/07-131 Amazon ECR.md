ao Amazon ECR.
Portanto, Amazon ECR significa
Elastic Container Registry, e é usado
para armazenar
e gerenciar imagens do Docker no AWS.
Até agora, temos usado repositórios on-line,
como o Docker hub, mas
também podemos armazenar nossas próprias
imagens no Amazon ECR.
E, na verdade, você tem duas opções para o ECR.
Podemos armazenar imagens de
forma privada, apenas
para sua conta ou para suas
próprias contas com
um s, ou você pode usar um repositório público e publicar
na galeria pública do Amazon ECR.
Agora o ECR está totalmente integrado
ao Amazon ECS, o
que é ótimo.
E suas imagens são
armazenadas nos bastidores
pelo Amazon S3.
Portanto, seu repositório
ECR pode conter diferentes imagens do Docker
e, em seguida, seu cluster ECS.
E, por exemplo,
uma instância EC2
em seu cluster ECS pode querer extrair
essas imagens.
Para isso, vamos
assinar uma função
do IAM em nossa instância
do EC2 e essa função do IAM permitirá
que nossa instância extraia imagens do
Docker.
Portanto, é claro que todo
o acesso ao ECR é protegido pelo IAM.
Isso inclui que, se houver um erro de
permissão no ECR, dê uma olhada
nas suas políticas e,
em seguida, os contêineres serão
iniciados na instância
do EC2 depois de serem puxados pela instância do EC2.
E é assim que o ECS
e o ECR ECR trabalham juntos.
Agora, o Amazon ECR é excelente
porque, além de
ser um repositório, ele oferece
suporte à varredura de vulnerabilidade
de imagem, controle de versão, tags de imagem e ciclo
de vida da imagem.
Portanto, em geral, sempre
que você vir o armazenamento de imagens do Docker, pense em ECR e
isso deve ser o suficiente
para você no exame.
Tudo bem.
Espero que você tenha gostado.
E eu o verei na próxima
palestra.
