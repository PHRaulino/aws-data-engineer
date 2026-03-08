E, na verdade, vamos reutilizar os mesmos dados que usamos para nossas avaliações de revistas da Amazon
na seção de banco de dados.
Portanto, se ainda não tiver feito esse exercício, talvez seja melhor voltar à seção de banco de dados
e fazer o exercício para usar o redshift, pelo menos até o ponto em que configuramos nosso bucket S3.
Ou você pode simplesmente acessar o site de materiais do curso aqui na Sundog Education. com slash AWS Data Engineer.
Há um link aqui para os materiais do curso, e a versão resumida é que você só quer criar
um bucket S3 com seu próprio nome exclusivo que contenha os metadados e as pastas de avaliações que
estão abaixo dos dados de avaliações de revistas nos materiais do curso.
Para esta atividade, usaremos apenas as próprias avaliações.
Portanto, este é um arquivo JSON de avaliações de assinaturas de revistas da Amazon. com.
E, no exercício anterior, analisamos essa estrutura e o que há nela.
Então, novamente, eu o incentivaria a voltar e fazer esse exercício para o redshift primeiro.
Se você ainda não o fez.
Tudo bem.
Portanto, se você tiver esses dados no S3, o que faremos neste exercício é usar o glue para extrair
alguma estrutura desses dados semiestruturados que estão no S3 e criar um esquema que possamos usar para
consultar esses dados como se fossem um banco de dados SQL do Amazon Athena.
O que é diferente é que, quando usamos isso no redshift anteriormente, copiamos esses dados para o redshift.
Desta vez, vamos apenas consultá-lo no local enquanto ele estiver no S3 como um lago de dados.
Portanto, você pode imaginar um mundo em que haja mais do que apenas um arquivo JSON aqui.
Talvez tivéssemos muitos arquivos JSON para diferentes categorias e talvez tivéssemos muitos arquivos JSON para revisões feitas em
momentos diferentes.
Certo?
Portanto, você pode imaginar que esse é um repositório muito maior de informações de revisão e não apenas um único arquivo.
Então, com isso, vamos para a cola e tentar extrair alguma estrutura desses dados semiestruturados.
Basta procurar por cola aqui Cola AWS.
Vamos criar um novo banco de dados, que é basicamente um banco de dados virtual.
Ele parecerá um banco de dados para o Athena e outras ferramentas, mas não está copiando dados de forma alguma.
Ele está apenas nos fornecendo um esquema em cima do nosso lago de dados no S3.
Então, vamos adicionar um banco de dados.
Vamos dar um nome a ele, vamos chamá-lo de revistas, e você pode dar uma descrição, se quiser.
Mas como sou preguiçoso, não vou digitar isso.
Criar banco de dados.
Agora, o que podemos fazer é acessar as tabelas e criar uma nova tabela para essas avaliações usando um rastreador.
Portanto, vamos configurar um rastreador de cola para dar uma olhada nos dados JSON e tentar inferir seu esquema.
Esse rastreador precisa de um nome, vamos chamá-lo de I don't know (Não sei).
Um rastreador de resenhas de revistas.
Novamente, você pode fazer uma descrição se quiser, mas eu sou preguiçoso.
Nossos dados não são mapeados em uma tabela de cola.
Esse é o ponto.
Queremos fazer um novo, então vamos mantê-lo.
Ainda não.
E adicione uma fonte de dados do S3.
Portanto, não precisamos de uma conexão de rede sofisticada.
Isso está nesse relato.
Vamos procurar no S3 a pasta em que ele se encontra.
Portanto, tome cuidado para não selecionar o próprio arquivo.
Isso não vai funcionar.
Parecerá que funcionou, mas não funcionará quando você tentar consultá-lo.
Portanto, é um caso muito sutil.
Portanto, o que quero fazer é selecionar a pasta de avaliações aqui e não o arquivo real dentro das avaliações.
Portanto, escolha isso.
Certifique-se de que ele tenha uma barra no final e que tudo esteja feliz, mesmo que isso tenha sido lido no início.
Se eu clicar fora disso, ele aceitará e será um caminho válido.
Agora, se tivéssemos subpastas, poderíamos dizer como lidar com isso.
Em um ambiente de data lake, as coisas podem ser particionadas, certo?
Você pode ter uma pasta para cada ano, e cada ano pode ter uma subpasta para cada dia.
Cada dia pode ter uma subpasta para cada hora, e assim por diante.
Nesse caso, temos apenas um nível, portanto, isso não é relevante.
Mas, em um cenário real com um lago de dados maior, isso seria algo a se pensar.
Vamos adicionar nossa fonte de dados S3 e clicar em next.
Precisamos atribuir a ele uma função de IAM.
Então, vamos criar um novo aqui.
Isso torna tudo muito fácil.
Basta dar a ele um sufixo.
Não sei, revistas, o que você quiser.
E isso lhe dará automaticamente as permissões necessárias.
Não estamos usando a formação de lagos aqui, portanto, não há nada para fazer lá.
E não estamos fazendo nada de especial com a criptografia em repouso para os logs do CloudWatch.
Então, vamos para a próxima.
Banco de dados de destino.
Vamos selecionar o da revista que acabamos de criar.
E não precisamos de um prefixo.
Mas se você quiser ter um prefixo de nome de tabela para classificar melhor as coisas, poderá fazer isso.
Além disso, se você se deparar com uma situação em que o cruel crawler esteja gerando toneladas e toneladas de tabelas,
às vezes ele se confunde com a partição.
Portanto, essa pode ser uma maneira de depurar isso e definir um limite, um limite superior de quantas tabelas
ele pode criar.
Às vezes, se ele não inferir a estrutura da partição corretamente, criará tabelas diferentes para cada partição
em vez de colocar tudo em uma única tabela.
Portanto, é para isso que ele existe.
Vou dizer para executar isso sob demanda, mas, novamente, no mundo real, você pode executar isso em um cronograma para coletar
novos dados automaticamente ou coletar alterações em seu esquema automaticamente.
Vamos falar sobre isso. A propósito, em Advanced Options (Opções avançadas), há algumas opções sobre o que fazer se
o esquema for alterado.
Portanto, você deve se lembrar que, na seção Fundamentos da engenharia de dados, falamos sobre o conceito
de evolução do esquema.
É disso que se trata.
Você está dizendo a ele como lidar com isso.
Se o esquema mudar, você poderá dizer o que mudou.
Faça o upload da definição da tabela para corresponder a ela.
Ou talvez apenas adicione novas colunas que você vê e não exclua as antigas.
Isso pode melhorar a compatibilidade com as consultas existentes, mas vamos manter isso como está, porque
meu esquema não vai mudar, e só vou executá-lo sob demanda porque não quero incorrer em custos
inesperados se eu esquecer de excluir esse rastreador quando terminar.
Então, vamos clicar em Avançar, revisar todas as configurações e criar o rastreador.
Mas ainda não terminei.
Preciso executá-lo.
Executar rastreador.
Ele está tentando iniciar.
Isso deve levar cerca de um minuto para ser concluído.
Muito bem, agora estamos em status de execução.
E eu poderia voltar quando isso terminar, mas acho que só vai levar mais uns 20
segundos.
Tudo bem.
Demorou um pouco mais do que eu esperava, mas terminou após cerca de um minuto, portanto, agora
está no status de concluído.
No entanto, às vezes isso é mentira, às vezes não é realmente feito escrevendo tudo.
Então, vamos voltar à seleção de rastreadores aqui.
E você pode ver que, na verdade, ele ainda não está pronto.
Ainda está em status de parada aqui.
Portanto, vamos esperar que isso aconteça.
Pronto e bem-sucedido para a última execução, pois ainda não terminou de escrever o esquema.
Mais alguns segundos e estará pronto.
Eigtht.
Tudo bem.
Na verdade, isso levou vários minutos.
Você nunca sabe o que vai conseguir com a AWS, não é mesmo?
Mas ele dizia pronto agora.
Então, vamos ver o que ele fez.
Vamos voltar aos nossos bancos de dados e selecionar o banco de dados da revista que criamos.
E agora há uma tabela de avaliações.
Sim.
Vamos dar uma olhada nisso e ver o que foi extraído.
Portanto, este é o esquema que ele criou.
Agora esse esquema é válido.
Isso se baseia nos dados JSON que encontrei.
No entanto, coisas como estruturas, estruturas aninhadas e matrizes não são bem mapeadas para colunas em um banco
de dados relacional.
Certo?
Portanto, em um pipeline de ETL real, se eu me importasse com essas informações, teria que transformá-las de
alguma forma e transformá-las em algo que pudesse ser apropriado para uma consulta SQL.
Se esse fosse o meu objetivo final, de fato consultar esses campos usando SQL.
Entretanto, minha tarefa aqui não requer essas informações.
Tudo o que eu realmente quero fazer é descobrir quem são os melhores avaliadores.
Esse é o nosso objetivo final aqui.
E, para isso, não preciso das imagens associadas a este item nem de nenhuma imagem associada à avaliação.
Em vez disso, não preciso dessa estrutura complicada do estilo da própria revisão.
Portanto, vou excluí-los.
Vamos clicar em editar esquema.
Selecione esses dois tipos de dados struct e array, que não serão bem mapeados para o Athena, e simplesmente exclua-os.
Se eu tentasse consultar o esquema como está, ocorreria
um erro e, bem, vamos tentar evitar isso.
Ei, meu esquema já evoluiu e todos eles parecem ser tipos de dados válidos que podem funcionar bem em uma configuração do
tipo SQL de banco de dados relacional.
Tudo bem.
Então, vamos voltar à exibição de tabelas aqui.
E preciso atualizá-lo.
Aqui está minha tabela de avaliações.
E você pode ver que aqui há um link útil para os dados da tabela.
Tudo o que isso faz é levá-lo a Athena.
Portanto, eu poderia clicar nesse link ou acessar o Athena no console para consultar esses dados.
Mas estou com preguiça, então vamos clicar no link.
Isso me avisa que estou saindo da cola e entrando no Athena, e o Athena tem seus próprios custos associados a ele.
Mas não se preocupe, isso não custará muito.
E, muito convenientemente, ele me forneceu uma consulta pré-gerada para fazer uma espécie de amostragem das dez primeiras linhas
desses dados e, veja só, temos dados.
Legal.
Uau.
Agora, se esta é a primeira vez que você está usando o Athena, talvez tenha recebido um erro sobre o destino de
saída ou algo assim. Não se preocupe, basta acessar a guia de configurações aqui em cima e, a partir daí, você poderá
gerenciar o local do resultado da consulta.
Você só precisa dizer a ele onde colocar os resultados no S3.
Portanto, clique em gerenciar e, a partir daí, você pode navegar para qualquer bucket S3 que tenha ou
criar um, se necessário, e clicar em salvar.
E isso é tudo o que você precisa fazer.
Depois disso, você pode voltar ao editor de consultas e executar a consulta novamente.
Incrível.
Portanto, mais uma vez, a pontuação geral da avaliação é de 1 a 5 estrelas.
Temos IDs e nomes de revisores exclusivos e os Asins que identificam a revista que estão revisando.
Muito legal.
Vamos fazer algo aqui.
Vamos fazer uma consulta.
Portanto, aqui está um pequeno desafio para você alongar seus músculos SQL.
Escreva uma consulta que identifique os principais avaliadores, e eu lhe darei uma chance.
Vá em frente e faça uma pausa se quiser resolver isso sozinho e volte quando tiver
terminado e puder compará-lo com a minha solução.
Caso contrário, vou apenas colar o que funcionou para mim.
Então, o que está acontecendo aqui?
Vamos prosseguir e executar isso.
Antes de mais nada, certifique-se de que ele realmente funciona.
Dê uma olhada.
Portanto, nosso principal avaliador foi Brian Carey, com 55 avaliações, seguido por Dale DK, com 26 avaliações.
Ei, a DK não é uma editora?
É bom que eles não estejam revisando suas próprias revistas.
Hmm hmm.
De qualquer forma, esta é a aparência da consulta.
Vamos agrupar tudo por ID do revisor e nome do revisor.
Estamos fazendo isso porque, se você deixar de fora o ID do revisor e agrupá-lo apenas pelo nome do revisor, alguns
revisores terão o mesmo nome.
Então, você sabe, Jane, por exemplo, pode aparecer com vários IDs de revisores diferentes ou Mike ou
Mark, certo?
Muitos deles usam apenas o primeiro nome.
Portanto, esse não é realmente um identificador exclusivo para um revisor, mas o ID do revisor é.
Portanto, ao aninhar esses itens, agrupando-os nesse ID de revisor aninhado e, em seguida, no nome do revisor.
Posso ver quando isso acontece, e não há nenhum exemplo real disso em meus resultados aqui, em que um determinado
ID de revisor nesses resultados principais é mapeado para mais de um nome.
Mas isso realmente proporciona melhores resultados.
Se eu agrupasse apenas pelo nome do revisor e não pelo ID do revisor, obteria um conjunto de resultados muito diferente
devido a esse problema.
E se eu agrupasse apenas o ID do avaliador em vez do nome do avaliador, bem, eu não teria nenhum nome e não
saberia quem são essas pessoas.
Por isso, fizemos dessa forma.
Temos esse agrupamento aninhado acontecendo aqui.
Então, vamos agrupar por ID do avaliador e nome do avaliador, ordenar pela contagem de avaliações, porque é nisso que estou
interessado.
Quem são os revisores mais prolíficos em ordem decrescente.
E para o que estou exibindo, vamos selecionar o ID do avaliador, o nome do avaliador e a contagem de avaliações
como contagem de avaliações.
Então, aí está o Athena em ação, consultando dados no local no S3 e no S3 Data Lake usando um esquema que criei
usando um rastreador de cola.
Agora é realmente possível carregar dados do S3 diretamente no Athena.
Você poderia dizer criar e criá-lo a partir dos dados do bucket do S3 sem envolver a cola diretamente.
Portanto, esse é um pequeno atalho.
Se você quiser usar apenas o Athena.
Mas o fato de ter esse esquema no catálogo de dados colados permite que eu consulte esses dados usando outras ferramentas, potencialmente.
Portanto, é bom ter isso.
Então, aí está.
Athena S3 glue, catálogo de dados de cola de rastreador de dados.
Tudo em ação lá.
Vamos limpar nossa bagunça, certo?
Não há nada para limpar no Athena, por si só, mas queremos acabar com esses recursos de cola.
Então, vamos voltar ao console de cola e excluir o banco de dados da revista.
Sim, tenho certeza.
Vamos excluir o rastreador também, por segurança.
Ação de exclusão do rastreador.
Certifique-se de que isso aconteceu.
Sim.
E o que resta?
As funções do IAM não custam nada.
Vou deixar isso para lá.
Mas vamos nos livrar desse bucket S3 se você também tiver terminado com ele.
Isso não vai lhe custar muito, mas custa alguma coisa.
Então, essa foi a minha.
DCO um Sundog, o seu é chamado de outra coisa.
Vamos excluí-lo.
Ah, ele precisa estar vazio primeiro, então não é tão simples assim.
Primeiro, temos que excluir tudo o que está dentro dele.
Excluir.
Permanentemente.
Excluir.
E também em metadados, excluiremos esse arquivo.
Isso é muito mais fácil com o uso de ferramentas de terceiros.
E agora devemos ser capazes de excluir todo esse bucket.
Como agora está vazio.
Excluir.
E eu preciso digitar o nome do balde para confirmar isso.
Sim, quero me livrar desses dados.
Tudo bem.
Conseguimos limpar nossa bagunça e ilustrar com sucesso o uso de um lago de dados e a consulta
a ele usando o Athena e o glue.
Muito legal.
