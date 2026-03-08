Então, vamos criar um novo
seguida, crio qualquer tipo de região e vou em frente e crio esse balde.
Em
Então, de volta ao meu balde, posso
ir em frente e carregar um objeto e clicar em adicionar arquivos.
Escolherei meu café. JPEG.
E vamos dar uma olhada nas opções.
Assim, podemos examinar as propriedades
desse objeto e, em classe
de armazenamento, obtenho uma ampla gama de classes de armazenamento
para objetos da AWS.
Portanto, temos o padrão S3, ok, e obtemos
o design de quatro colunas.
Quantos AZs temos, bem como alguns outros
(indistintos), a duração mínima do armazenamento,
o tamanho mínimo do objeto faturável
e as taxas de monitoramento e de divisão
automática em camadas.
Então, vamos dar uma olhada em todos eles.
Portanto, temos o padrão, que são os básicos por padrão.
Em seguida, temos a classificação inteligente,
caso não conheçamos nossos padrões de dados e, portanto,
queremos que o AWS execute a classificação
de dados para nós.
Standard-IA, se quisermos que os dados sejam acessados com pouca
frequência, mas ainda com baixa latência.
One-Zone-IA, ou
seja, você pode recriar esses dados,
e eles serão armazenados em apenas um AZ.
E, portanto, você
pode correr o risco de perder o objeto,
se o AZ for destruído.
Depois, temos três níveis de geleira.
Portanto, temos o Glacier Instant Retrieval,
o Glacier Flexible Retrieval ou o
Glacier Deep Archive, e ele
informa exatamente quais
são as condições aqui.
E, por fim, Reduced Redundancy,
que é um tipo de camada de armazenamento obsoleto e, portanto,
não o descrevi no curso.
Então, e se usarmos a IA padrão,
por exemplo, e criarmos um objeto lá?
Portanto, estamos indo para
lá e depois faremos o upload.
De volta ao nosso balde.
Portanto, agora esse objeto tem a classe de armazenamento, Standard-IA,
como mostrado aqui.
Mas o que eu posso
fazer é mudar a classe de armazenamento,
se eu quiser.
Portanto, posso acessar as propriedades e rolar para
baixo, e podemos editar a classe de armazenamento
para fazer algo diferente.
Assim, podemos movê-lo, por
exemplo, para One-Zone-IA,
caso em que esse objeto será
armazenado em apenas uma zona.
Então, vamos salvar essas alterações.
E agora meu objeto foi editado com sucesso e, portanto,
a classe do objeto foi alterada.
Portanto, se rolarmos a tela para baixo, agora estamos na One-Zone-IA.
E, novamente, você pode editá-lo
e ir, por exemplo, para Glacier-Instant-Retrieval.
E agora ele será arquivado, ou
você pode optar pelo Intelligent-Tiering,
e ele poderá ser automaticamente definido
para o nível certo com base em nossos padrões, e assim por diante.
Portanto, você pode ver que há muito poder usando classes de armazenamento.
E, por fim, quero mostrar
a você como podemos automatizar a movimentação desses objetos entre
as diferentes classes de armazenamento.
Então, vamos voltar
aos nossos compartimentos e, em gerenciamento, você
pode criar regras de ciclo de vida.
E você pode criar uma
regra, que chamaremos de "DemoRule". E então você dirá: "ei", aplique
a todos os objetos
nos compartimentos.
Sim, claro.
E então podemos dizer, ok, mover
as versões atuais entre as classes de armazenamento.
E você está dizendo, ei,
você vai para o Standard-IA depois de, por exemplo, 30 dias.
E, depois de 60 dias, você passa para o Intelligent-Tiering.
Em seguida, você passaria para o Glacier-Flexible-Retrieval
após 180 dias, e assim por diante.
Assim, você tem algumas transições.
E aqui você pode revisar todas
as transições que fez.
Portanto, é possível
automatizar a movimentação de objetos entre camadas.
Está bem. Então é isso, já vimos
tudo o que precisamos saber sobre classes de armazenamento.
Espero que você tenha gostado.
E eu o verei na próxima palestra.
