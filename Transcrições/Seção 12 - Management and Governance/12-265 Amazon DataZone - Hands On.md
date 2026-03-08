Vamos brincar com o Amazon Datazone.
E vou usar alguns dados reais para isso.
Então, só para explicar, minha esposa e eu temos uma estação de rádio on-line chamada Radio Calico.
E, no final de cada mês, temos que enviar um relatório de uso para pagar basicamente os direitos autorais de todas as
músicas.
A aparência é a seguinte.
Portanto, esses são os dados com os quais vamos trabalhar.
É assim que se parece um relatório real de royalties.
Portanto, ele contém basicamente todas as músicas que tocamos durante todo o mês.
É o número de identificação e quantas vezes foi ouvido por diferentes pessoas ao longo do mês.
Então, vamos começar.
Em primeiro lugar, vamos acessar o Datazone no console.
E a primeira coisa que você vai notar é que a Datazone tem uma espécie de personalidade dividida no momento.
Portanto, há o serviço legado do Datazone que é chamado apenas de Amazon Datazone, mas eles estão implementando-o no Amazon
SageMaker Unified Studio agora, e eu não ficaria surpreso se, em algum momento, eles descontinuassem a antiga interface
de usuário original do Datazone em favor do SageMaker.
Ainda não houve nenhum anúncio sobre isso.
Mas, apesar de ser um serviço relativamente novo, não me surpreenderia se fosse esse o caminho.
No entanto, estou ensinando a você o que será abordado no exame e, no momento, isso é o datazone, mais ou
menos em sua forma clássica.
Então, vamos clicar em criar um domínio Amazon Datazone em vez de um domínio de estúdio unificado.
Mas lembre-se de que tudo o que estamos fazendo aqui também pode ser feito nos domínios unificados do SageMaker.
Tudo bem.
A propósito, primeiro precisamos notar que ele já está no SageMaker.
Portanto, acho que isso pode ser um indício do que está por vir.
Portanto, um domínio é novamente o tipo de organização de alto nível que usará esses dados.
Portanto, vamos chamar essa rádio de Calico, pois esse é o nome da organização que a está usando, e
a descrição será a que você quiser.
Um relatório de dados de uso e outras coisas, sabe como é.
Certo.
Tudo bem.
Vamos usar a função de execução de domínio padrão.
Não tem problema.
Queremos ter certeza de que vamos configurar isso para permitir o consumo e a publicação de dados para
todos os usuários.
Dessa forma, podemos publicar e assinar dados facilmente em nossa pequena demonstração aqui, e permitiremos que ele use
suas próprias funções de serviço que ele mesmo cria para essa finalidade.
Tudo bem.
Portanto, não há muito o que fazer aqui.
Observe que ele criará um bucket S3 para você como parte do processo.
E quando você exclui esse domínio, a propósito, isso não desaparece.
Portanto, se você quiser fazer a limpeza mais tarde.
Não se esqueça de voltar e excluir esse bucket S3 quando terminar.
Vamos clicar em criar domínio e aguardar a conclusão.
Demora um minuto ou mais, mas não muito.
Mas vou cortar e voltar quando isso for feito.
Tudo bem, isso não demorou muito.
Portanto, aqui temos nosso domínio.
E uma coisa que você geralmente quer fazer não é estritamente necessária para o que vou mostrar a você hoje.
Mas uma boa ideia é ir até as plantas e alterar algumas coisas.
Portanto, antes de começarmos, vamos ver as plantas.
Lembre-se de que falamos sobre isso nos slides.
Portanto, por padrão, o blueprint do data lake padrão está ativado e o Default data Warehouse está ativado.
E poderemos escolher entre eles quando criarmos nossos ambientes mais tarde.
Mas vamos editar um pouco o projeto padrão do data lake.
E vamos ao provisionamento.
E isso pode evitar um pouco de problemas no futuro se você ativar essa opção de
registro de locais com a formação do AWS Lake aqui.
Caso contrário, você terá todos os tipos de problemas estranhos, com todas essas questões
de permissões quando estiver tentando acessar os dados de fora do Datazone, que provavelmente é onde estão
seus dados, certo?
Portanto, vale a pena fazer isso.
Basta clicar em editar e habilitar essa opção para permitir que o Datazone se encarregue de registrar os locais
do S3 com formação de lago, modo de acesso híbrido, e isso lhe poupará muitos problemas.
E vamos prosseguir e permitir que ele use uma nova função de serviço.
Acho que já tenho um, então isso pode me dar um erro.
Vamos descobrir.
Sim.
Portanto, tenho que usar um já existente porque já fiz isso antes.
Mas, para você, isso provavelmente é bom.
Vamos nos livrar desses erros porque eles são feios.
Tudo bem.
Portanto, temos nosso domínio pronto para ser usado.
Vamos voltar ao nível superior disso.
E vamos abrir nosso portal de dados.
Portanto, novamente o portal de dados está fora do console real.
Trata-se de um pequeno aplicativo da Web próprio que pode ser executado sem a necessidade de estar no console do AWS.
Portanto, aqui está um link prático para ele.
Aguarde até que ele gire.
Tudo bem.
Então, vamos começar criando um novo projeto.
Agora, o que vamos fazer é criar dois projetos.
Um para publicar os dados.
Portanto, ele simulará um tipo de grupo de pessoas, como uma equipe responsável pela curadoria dos
próprios dados.
Em seguida, criaremos um segundo projeto para consumir esses dados e, de fato, fazer análises sobre eles.
Então, vamos começar dizendo criar um novo projeto.
Vamos dar um nome a ele.
Vamos chamá-lo de, hum, não sei, relatório de uso, hum, publicar ou algo do gênero.
E, para uma descrição, podemos dizer fontes de dados de rádio calico ou algo assim, o que você quiser.
E você precisa selecionar o domínio que está associado a esse projeto.
Portanto, crie um projeto.
E agora precisamos criar um ambiente, já que temos nosso projeto.
Portanto, lembre-se de que os ambientes estão em projetos.
E vamos dar um nome a esse ambiente também.
Vamos chamá-lo de editor de rádio calico, o que for.
Sempre.
E você pode dar uma descrição, se quiser.
E aqui vamos selecionar esse projeto.
Então, aqui embaixo, vamos dizer perfil do Data Lake.
Porque, no final das contas, estarei importando dados do Amazon Athena.
Como você verá em breve.
E podemos deixar todos os nomes padrão para os vários glue databases e grupos de trabalho do jeito que estão.
Não tem problema.
Vamos clicar em Create Environment e isso também levará cerca de um minuto.
Portanto, vamos esperar que isso aconteça.
E voltarei quando isso for feito.
Tudo bem.
Temos nosso ambiente aqui.
Então, vamos criar uma tabela para publicar por meio dela.
Então, vou clicar neste botão para consultar os dados com o Amazon Athena.
E um efeito colateral um pouco irritante de apertar esse botão é que ele vai me desconectar
da minha conta do AWS e me conectar como o usuário associado a esse front-end que estamos usando agora, o portal de
dados.
E ele diz que você tem certeza disso?
Sim, tudo bem.
Não há problema.
Tudo bem.
Portanto, para facilitar um pouco a vida, em vez de obrigá-lo a configurar um bucket S3 cheio de dados e outras
coisas.
Estou apenas lhe fornecendo alguns dados de amostra no formato SQL bruto.
Portanto, se você acessar os materiais do curso, se estiver acompanhando o curso, deverá ter um ponto de dados de amostra da zona
de dados.
TXT lá.
E você pode ver que essa é apenas uma instrução padrão do tipo create table as select para criar
uma nova tabela chamada Sundog music data usando as seguintes linhas codificadas a partir desses dados reais.
Portanto, apenas alguns dados de amostra aqui.
E vamos fazer isso desta forma.
Apenas para evitar o trabalho de criar um bucket S3 e gerenciar todas as permissões para garantir que o sistema
subjacente de formação de lagos que está sendo executado por trás do Datazone possa acessar esse bucket S3.
Isso pode se tornar muito, muito desagradável.
Portanto, se você tiver problemas no mundo real, há algumas instruções muito específicas no guia do usuário
do Datazone para contornar esse problema.
E mesmo esses são um pouco difíceis de acompanhar.
Mas, de qualquer forma, vamos copiar e colar isso só para evitar problemas e executar
isso.
E agora temos uma tabela de dados de música do Sundog.
Agora, se voltarmos ao Datazone e clicarmos em dados.
Clique em Data sources (Fontes de dados) e selecione a fonte de dados padrão que foi criada.
E agora, se clicarmos no botão Executar, ele deverá procurar a tabela que acabamos de criar.
Mas pode demorar um pouco.
E aí está.
Vamos selecionar isso.
E agora estamos no catálogo de dados comerciais.
Portanto, você pode ver que não sabe muito sobre isso, exceto pelos dados brutos reais.
Mas ele pode adivinhar.
Portanto, ele conhece o esquema.
E apenas com base nos nomes dessas colunas, ele fará o melhor possível usando IA.
Se você quiser economizar o trabalho de escrever tudo isso.
Portanto, clique no botão Generate Descriptions (Gerar descrições) e aguarde a conclusão.
Não é legal?
Portanto, você pode analisar tudo isso e ver se faz sentido.
Na verdade, ele é bastante preciso, honestamente.
É surpreendentemente bom.
Portanto, vamos em frente e aceitamos isso.
Obviamente, no mundo real, você realmente gostaria de ler isso e ter certeza de que concorda com isso.
Além disso, aqui em cima, vou dizer "aceitar tudo" para todos os outros metadados gerados por IA.
E ele apresentou um nome comercial, nomes de colunas e descrições comerciais para todas as colunas.
E se você acessar o esquema, poderá ver quais são eles.
Portanto, faz sentido.
Você sabe, ele simplesmente pegou os nomes das colunas subjacentes e os transformou em algo
mais legível e extraiu uma descrição deles.
Novamente, é óbvio que você deve se certificar de que esses dados são realmente precisos antes de aceitá-los.
E é claro que você pode editá-los se quiser.
Tudo bem.
Portanto, agora que estamos satisfeitos com os dados reais, podemos clicar em Publish Asset (Publicar ativo).
E sim, quero publicá-lo.
E isso foi publicado com sucesso.
Muito legal.
Tudo bem.
Então, agora vamos criar esse segundo projeto e simular um segundo conjunto de usuários que talvez queiram
consumir esses dados e criar relatórios a partir deles.
Portanto, eles não precisam de acesso para gerar os dados em si.
Eles só querem usá-lo.
Esse menu suspenso permite que você selecione o projeto no qual deseja trabalhar.
E eu só tenho um.
Portanto, vamos criar um novo projeto e chamá-lo, não sei, de Report of use analytics ou algo assim.
Hum, eu faço consultas, tanto faz.
Novamente, você precisa selecionar o domínio e criar o projeto.
E, assim como antes, precisamos criar um ambiente e dar um nome a ele.
Análises de rádio calico.
E ou qualquer outra coisa.
Faça uma descrição, se quiser.
E, novamente, você precisa selecionar um perfil.
E, mais uma vez, usaremos o perfil do lago de dados porque é o que estamos usando e criando o ambiente.
Novamente, vamos deixar isso funcionar por um minuto enquanto ele cria todos os seus recursos subjacentes.
Tudo bem.
Isso funcionou.
Está bem.
Então, vamos comprar alguns dados, certo?
Para fazer isso, podemos usar a barra de pesquisa aqui em cima e procurar os dados que desejamos.
Assim, podemos pesquisar qualquer coisa que possa estar associada a esse conjunto de dados, como um isrc.
É o nome de uma das colunas que, na verdade, pode ser o suficiente para trazer o assunto à tona.
E assim é.
Portanto, um conjunto de dados que realmente corresponde a isso é o catálogo de conteúdo musical, que é o que acabamos
de publicar.
E podemos ir até aqui e ler tudo sobre ele, ver seu esquema, sua linhagem e tudo o mais,
embora não haja muito disso agora.
No entanto, ele informa o que realmente aconteceu.
Então, você sabe, passamos dos dados brutos para o que publicamos lá.
E se dissermos: "Sim, esses são os dados que eu quero", podemos nos inscrever, mas precisamos pedir permissão primeiro.
Portanto, a Datazone não permitirá que qualquer pessoa use seus dados.
Eles precisam solicitá-lo, e você precisa aprovar manualmente esse uso e a quantidade de acesso que deseja conceder
a eles.
Então, vou dizer: "Gostaria de usar esses dados, por favor".
E você precisa dar a eles um motivo.
Hum, porque eu quero.
E podemos fazer a solicitação.
Tudo bem.
Portanto, a solicitação de assinatura foi criada.
Então, vamos voltar ao projeto do editor original e fingir que somos a pessoa que realmente publicou
esses dados.
Portanto, nesse menu suspenso, voltarei para Report Reviews Publisher e clicarei em View Incoming Requests (Exibir solicitações
recebidas).
E podemos ver que, de fato, as visualizações relatadas do Analytics querem meus dados.
Eles pediram permissão.
Então, vamos visualizar essa solicitação e decidir se queremos dar permissão a eles.
Eu direi que está bem, sim, você é legal.
Hum, nós lhe daremos acesso total e escreveremos o que você quiser em resposta.
Muito bem.
Você pode ter seus dados e aprová-los.
Tudo bem.
Portanto, isso foi aprovado.
Agora podemos voltar a fingir que somos o cliente do Analytics.
Suas visualizações de relatórios analíticos fazem login nesse projeto.
E agora podemos consultar esses dados usando o conjunto de dados que assinamos no outro projeto.
Então, vamos clicar em Query Data with Amazon Athena (Consultar dados com o Amazon Athena).
E sim, eu sei que você vai me desconectar.
Portanto, agora devo poder ver esse banco de dados no menu suspenso aqui, abaixo das assinaturas.
Sim.
Então, veja o que eu fiz.
Como se eu fosse uma conta de assinante lá.
Então, mudei o banco de dados para o subbanco de dados.
E lá embaixo, vejo a tabela de dados de música do Sundog para a qual recebi permissão.
Então, com certeza, há dados lá e podemos fazer consultas com eles, como, por exemplo, não sei,
selecionar estrela dos dados de música do Sundog.
Deixe como está.
E, com certeza, temos dados.
Não é legal?
Tudo bem.
Esse é um exemplo rápido de como usar o Datazone em um ambiente de data lake, usando o Athena, o glue e tudo o que estiver
nos bastidores.
Mas vamos nos certificar de que limpamos a bagunça que fizemos.
Portanto, vou sair do Athena e do Datazone também, e teremos que fazer login novamente no console para limpar
a bagunça do domínio real do Datazone, portanto, voltarei depois de fazer login novamente.
Muito bem, depois de sair da conta do datazone para o portal de dados.
Estou de volta à minha conta principal real da AWS e, por qualquer motivo, o Datazone nunca aparece e foi visitado recentemente,
mas vamos digitar Datazone novamente para voltar a ele.
E apenas para limpar a bagunça, vamos selecionar esse domínio e excluí-lo.
E precisamos confirmar que realmente queremos fazer isso.
E ele avisa que ainda há muitos recursos que serão deixados para trás.
Portanto, o próprio domínio será destruído.
Mas, sob o capô, provavelmente ainda há uma caçamba S3 da qual você pode querer se livrar.
Haverá um monte de material restante na cola de formação de lagos.
Portanto, sim, se você quiser ser cuidadoso, talvez seja melhor procurar tudo isso, mas não
deve ser nada que lhe gere despesas.
Tudo bem.
Esse é o datazone em poucas palavras.
E, novamente, você sabe, isso está se movendo em direção ao SageMaker como parte do SageMaker Unified Studio.
E se, em algum momento, eles realmente descontinuarem a interface do usuário que acabei de mostrar e que o Datazone tinha
originalmente como um projeto autônomo.
Vou atualizar esta palestra com certeza, mas se você perceber isso antes, deixe uma mensagem nas perguntas e respostas
desta palestra para me avisar.
