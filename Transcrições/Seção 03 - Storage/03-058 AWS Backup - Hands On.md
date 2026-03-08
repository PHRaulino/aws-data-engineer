Ok, então vamos praticar o uso do AWS Backup.
o serviço de backup.
Portanto, vamos criar nosso primeiro plano de backup.
Então, vou clicar em Create Backup plan (Criar plano de backup).
E temos três opções.
Começamos com um modelo ou criamos um novo plano, ou
definimos um plano usando JSON.
Portanto, o mais simples para nós é começar com um modelo, e podemos
ter modelos diferentes.
Por exemplo, Daily-35day-Retention (retenção diária de 35 dias), Daily-Monthly-1yr-Retention
(retenção diária mensal de 1 ano) e assim por diante.
Portanto, vamos usar Daily-Monthly-1yr-Retention,
e eu o chamarei de TestPlan.
Em seguida, clicamos em Backup rules (Regras de backup).
E você vê que podemos ter muitas regras de backup
em nossas regras de backup.
Portanto, temos dois: backups diários e mensais.
Portanto, se eu clicar em Daily Backup, como
podemos ver, há um nome de regra.
O cofre de backup é o local para onde o backup está indo.
Portanto, podemos usar um padrão da AWS ou criar
nosso próprio cofre de backup, se quisermos.
A frequência de backup, a janela de backup, quando começar, que
é às 5:00 AM UTC, começa dentro de oito horas, ou você pode personalizá-la,
se quiser.
Se você deseja ou não fazer a transição para o armazenamento
a frio, nunca, depois de alguns dias, semanas, meses ou anos.
E o período de retenção de seu
backup, por exemplo, este é retido por cinco semanas.
Em seguida, também podemos copiar esses backups
para um destino específico.
Por exemplo, outra região para fins de recuperação de desastres.
Portanto, vou salvar essa regra de backup.
E, mensalmente, recebemos algo semelhante, portanto,
ele está indo para o cofre de backup padrão.
É mensal no primeiro dia de cada mês, e
o restante é igual.
Então, na verdade, fazemos a transição desses produtos
para o armazenamento a frio depois de um mês e, em seguida, os mantemos por um ano.
Pronto, já temos tudo pronto e, então,
posso rolar a tela para baixo e clicar em criar plano.
Portanto, agora nosso plano de teste foi criado e precisamos
atribuir recursos a ele.
Então, vou clicar em atribuir recursos
e vou chamá-lo de TestAssignments.
Portanto, aqui para a função
IAM, usaremos a função padrão,
que criará uma função para nós com as permissões
corretas, ou você pode escolher a sua própria, mas
vamos usar a função padrão, fácil.
E, para a seleção de recursos,
há duas coisas que podemos fazer.
Em primeiro lugar, podemos incluir todos os tipos de recursos ou, em segundo
lugar, podemos incluir tipos de recursos específicos.
Por exemplo, se você quisesse ter apenas uma tabela do DynamoDB
e depois selecionar o recurso desejado nela, poderia
fazer isso.
Ou, se você quiser, pode ter todas as mesas.
Portanto, essa é uma maneira de fazer isso.
Ou, se você optar por todos os tipos de recursos, normalmente
usaremos isso como uma combinação com tags.
Assim, no caso das tags, você
diria: "Bem, se o ambiente principal for igual à produção de valor, então
faça um backup".
Esse seria o tipo de caso de uso para backups,
mas você é livre para fazer o que quiser, é claro.
E, quando terminar, clique em atribuir recursos.
Então, só para deixar bem claro,
se eu entrasse no EC2 e criasse um volume EBS, esse
volume teria, por exemplo, um gigabyte
e a chave seria environment production.
Em seguida, o backup seria feito automaticamente pelo meu plano de backup
porque ele tem as tags corretas.
Portanto, se olharmos para o nosso volume
agora e entrarmos nas tags,
como podemos ver, ele tem o ambiente de produção,
que corresponde às tags que configurei para
o meu plano de backup, certo?
Portanto, essas são as atribuições aqui.
E também podemos ter várias atribuições aqui. Está bem?
E então é isso.
O plano de backup será executado automaticamente
e, em seguida, os backups ocorrerão aqui
em meus cofres de backup, certo?
Os trabalhos são os trabalhos que serão agendados e que
acontecerão.
Portanto, temos trabalhos de backup,
restauração e cópia, se quisermos.
Em seguida, podemos examinar as configurações.
Portanto, as configurações estão relacionadas
a se você deseja ter políticas de backup, monitoramento
entre contas, backups entre contas
e assim por diante.
Mas já vimos os princípios básicos de como os backups funcionam.
E é isso.
Quero lhe mostrar tudo isso, ok?
Isso é tudo o que você precisa saber.
E vou excluir tudo.
Portanto, para isso, certifique-se de excluir o volume do EBS ou
aguarde um dia se
quiser ver se os backups funcionam, obviamente.
E, quando terminar, você
pega as atribuições e as exclui.
Portanto, digite o nome da atribuição aqui e, em seguida, para as regras de
backup diário, você pode excluí-las
ou excluir diretamente o plano de backup.
Para isso, basta digitar o nome do plano de backup
e pressionar delete.
E é isso.
Já vimos backups.
Espero que tenham gostado e nos veremos na próxima palestra.
