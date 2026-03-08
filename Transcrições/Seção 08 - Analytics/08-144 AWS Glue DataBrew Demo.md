Então, vamos explorar um pouco o Glue
DataBrew aqui.
Mais uma vez, farei um pequeno tour rápido
pela interface do usuário para tornar um pouco
mais intuitivo o que se trata.
Então, estou na página do console do Glue DataBrew
e vamos criar um projeto de amostra usando apenas alguns
dos dados de amostra que eles fornecem.
Vamos explorar os nomes populares para bebês em 2020.
E criaremos um novo projeto no DataBrew para isso.
Precisamos atribuir a ele uma função
de IAM para fins de segurança.
Vamos usar este que já criei e ele
vai provisionar alguns recursos de computação
para executar esta seção interativa do DataBrew
neste conjunto de dados.
Como você se lembra do processamento,
é US$ 1 por sessão interativa e, se você quiser
executar isso como um trabalho contínuo, isso será cobrado pelos
recursos que você usar.
Mas, por enquanto,
ele vai aumentar alguns recursos de computação rapidamente.
Ele iniciará minha sessão de DataBrew a qualquer momento.
Na verdade, isso acontece muito rapidamente.
Não é como criar um nó EC2 ou algo do gênero.
E aqui vamos nós.
Ele está preparando um quadro de dados a partir desses dados
de amostra, carregando-os do S3.
E estamos prontos para o rock and roll aqui.
Assim, você pode ver que temos essa visualização
de quadro de dados dos dados de amostra aqui,
onde temos quantas vezes cada nome de bebê apareceu,
o gênero, algum ID associado a ele, o próprio nome
e um campo de ano, que é 1880.
Achei que esse era um conjunto de dados
de 2020, mas não vou entrar nesse assunto agora.
De qualquer forma, a ideia aqui é que você possa aplicar essas receitas
e construí-las para transformar esses dados
da maneira que desejar, podendo executá-las
interativamente e baixar os resultados, ou criar um trabalho
que permita executá-las repetidamente e até mesmo executá-las em uma
programação.
Por exemplo, digamos que eu só queira obter nomes de bebês que comecem com a letra
L por algum motivo, apenas como
um exemplo bem simples.
Vamos criar uma nova receita aqui.
Assim, podemos adicionar uma etapa à nossa receita, e aqui está o menu
de todas as diferentes transformações que você
pode realizar.
Em mais de 250 deles, há ações de coluna.
Você pode renomear colunas ou alterar seus
tipos, movê-las, duplicá-las ou excluí-las.
Você pode filtrar as coisas, o que faremos.
Você pode alterar a formatação dos campos de texto.
Há operações de limpeza de dados incorporadas aqui.
Portanto, se você quiser remover caracteres
especiais ou números, o que quer que queira
fazer, se precisar preparar isso antes do processamento posterior, poderá
fazer isso facilmente com os filtros limpos.
Também podemos extrair informações entre os delimitadores.
Portanto, se você tiver um campo com dados delimitados
e quiser apenas extrair dados entre esses
delimitadores, isso é fácil de fazer.
Você pode simplesmente especificar quais são os delimitadores
e onde deseja colocar essa coluna, certo?
É uma maneira muito fácil de fazer isso.
Além disso, você pode imputar automaticamente os valores ausentes.
Esse é um recurso interessante.
Então, o que você quer fazer se os dados estiverem faltando?
Você quer preenchê-lo apenas com valores nulos ou vazios?
Você deseja excluir a linha completamente?
Ou talvez você queira apenas preenchê-lo
com o valor mais frequente como um espaço reservado.
Às vezes, essa é a coisa certa a fazer.
Muito fácil de fazer no DataBrew.
O que mais podemos fazer?
Valores inválidos, você pode lidar com isso.
Você pode lidar com valores duplicados da maneira que desejar.
Você pode dividir colunas, mesclá-las,
criar novas colunas com base em algum tipo de função, unnests
pivot, group by, join union.
Agora estamos entrando em operações do tipo SQL, certo?
Portanto, praticamente tudo o que você
pode fazer em um banco de dados pode ser feito no DataBrew, podemos dimensionar
valores numéricos.
Isso pode ser muito útil se você
estiver preparando dados para a aprendizagem profunda, certo?
Muitas vezes, é necessário normalizar esses
dados antes de alimentá-los em uma rede neural.
E essas operações de dimensionamento tornam isso muito fácil de fazer.
O que mais temos? Agregados, funções de texto.
Basicamente, todas essas são funções SQL disponíveis
para você, e isso elimina muitas das
250 opções existentes.
Mas você pode ver que praticamente qualquer transformação
que queira fazer está aqui.
Isso é muito legal.
Ele permite que você tenha um mecanismo
muito dimensionável e avançado para transformar
e pré-processar dados que, em geral, não
envolvem a gravação de nenhum código.
Muito legal.
Então, digamos que queremos filtrar os dados para
obter apenas nomes de bebês que comecem com a letra L.
Portanto, direi filtrar por
condição, selecionaremos a coluna
Nome e diremos que ela deve começar com L.
E posso visualizar isso com
o botão de visualização aqui.
E você pode ver que apenas os nomes de bebês que começam
com L foram preservados.
Muito legal.
Em seguida, posso aplicar isso a todo o conjunto de dados.
E agora temos um conjunto de dados de nomes
de bebês que começam com a letra L.
Muito legal.
Você verá que há atalhos para muitos deles
aqui no painel.
E o que posso fazer? Vamos para Ações.
Assim, posso fazer o download dos dados filtrados como
um arquivo CSV, o que é muito bom, ou posso criar um novo
trabalho a partir dele se quiser
executá-lo repetidamente.
Isso me levará até a guia Jobs aqui.
Eu poderia criar um nome de
trabalho para ele, então BabyNames-L, como você quiser chamá-lo.
E podemos definir as configurações de saída aqui.
Portanto, os tipos de arquivo que você pode
gerar no momento são um pouco limitados, mas
podem ser CSV, Glue Parquet, Parquet, Avro, ORC, XML ou JSON.
Essas são as opções de saída atuais
para o bucket S3 de sua escolha e a compactação
de sua escolha.
Snappy, Gzip, LZ, Bzip ou Deflate e Brotli.
Esses são dois novos.
Qualquer delimitador que você queira,
separado por vírgula, separado por dois pontos, separado
por tabulação, qualquer coisa que você possa imaginar aqui.
E, sim, depois de ter isso,
você pode executar esse trabalho como algo sob demanda ou pode criar
uma programação para ele.
Se você voltar ao console do DataBrew aqui e for para Jobs, poderá clicar
na guia Schedules (Agendamentos), e é aqui que você criaria um agendamento
para executar um trabalho repetidamente
em algum tipo de agendamento
no estilo cron, portanto, você também pode
fazer isso.
Novamente, voltando à guia principal Pricing aqui.
Atualmente, essas sessões interativas
custam apenas US$ 1 por sessão, mas se você
quiser criar um trabalho e executá-lo
repetidamente, ele será cobrado a 48 centavos de dólar por hora de nó para
esse custo de processamento.
E se você quiser calcular
isso, há uma calculadora de custos bem útil.
Em resumo, esse é o DataBrew.
Como você pode ver, todo o propósito de
sua existência é fornecer uma maneira muito fácil de pré-processar dados
de forma muito escalonável e muito rápida, sem escrever
nenhum código.
E é um recurso relativamente novo e possivelmente
uma alternativa ao uso do Glue ETL para você.
