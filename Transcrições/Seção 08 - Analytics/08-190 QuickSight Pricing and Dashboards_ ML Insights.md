QuickSight e, mais uma vez, por ser voltado para usuários finais
comuns e não para desenvolvedores, eles não cobrarão
com base em coisas como número de consultas, espaço de armazenamento ou coisas do
gênero.
É de nível superior, assim como o restante do serviço.
Portanto, há duas opções.
Você pode fazer uma assinatura anual,
em que economiza algum dinheiro ao se inscrever para um ano
inteiro e eles cobram por usuário, por mês, certo?
Portanto, para cada usuário do seu plano do QuickSight, se
você estiver usando a edição
padrão, são US$ 9 por usuário por mês.
E para o plano empresarial, são US$ 18 por usuário por mês.
E há também outro recurso chamado QuickSight Queue, que
é uma interface de processamento de linguagem
natural sobre o QuickSight.
Ainda não conversamos sobre isso, mas o faremos em breve.
Isso custa ainda mais, ou seja, US$ 28 por usuário por mês.
Se você precisar de capacidade SPICE adicional,
é aqui que as coisas ficam um pouco mais técnicas.
Se você precisar de mais de 10 gigabytes dessa capacidade
do SPICE para acelerar suas consultas, serão cobrados 25 centavos
de dólar no plano padrão ou 38 centavos de
dólar no plano corporativo por gigabyte por mês.
Mas, novamente, isso só será um problema se você tiver
conjuntos de dados realmente enormes, certo?
Você também pode assinar mês a mês
e eles cobrarão mais pelo privilégio.
US$ 12 por usuário por mês para o plano
padrão, US$ 24 para o plano empresarial.
E se você quiser os recursos de processamento de
linguagem natural além do QuickSight com
o QuickSight Queue, o valor será de US$ 34 por usuário por mês.
Só para lembrar, o que você recebe com a edição enterprise.
Isso proporciona criptografia em repouso para
seus dados e para os resultados exportados no QuickSight,
além de integração com o Microsoft
Active Directory.
Um recurso importante do QuickSight são os painéis
e, se você já fez alguma análise de dados, sabe o
que é um painel.
Exatamente o que parece.
É um instantâneo somente para leitura de sua análise
que você pode apresentar em forma de gráfico para as
pessoas, permitindo que elas naveguem
por vários quadros, gráficos e números importantes
associados ao que lhe interessa e apresente tudo isso de forma compacta
aos proprietários da empresa para que eles possam realmente fazer algo com essas informações.
Os painéis, é claro, podem ser compartilhados
com outros usuários do QuickSight.
No entanto, eles precisam ter acesso
ao QuickSight e ser configurados como usuários
no QuickSight, porque o QuickSight cobra pelo uso
e por quem o está usando.
Agora, além de ver seus painéis por meio do próprio
QuickSight, eles também têm
algo chamado painéis incorporados.
Assim, você pode compartilhar essas coisas ainda mais amplamente
em seus próprios aplicativos.
Assim, com os painéis incorporados, você recebe um SDK JavaScript e uma
API que permite incorporar esse painel alimentado pelo QuickSight
em algum aplicativo que você oferece às pessoas.
Pode ser um aplicativo móvel, pode ser um aplicativo da Web,
não sei, mas é uma forma de incorporar os painéis
do QuickSight em outros aplicativos.
Como isso funciona?
O principal problema que você pode pensar
é: "Bem, como o QuickSight me cobra por isso se o QuickSight
se baseia no uso e me cobra pelo uso, A, como ele sabe
quem o está usando?
E B, como evito que todos no mundo acessem meu painel do QuickSight
por meio de algum aplicativo e eu seja cobrado
por todos no mundo? Portanto, há muita
autenticação para fazer com que
os painéis incorporados funcionem.
Agora, para que tudo seja perfeito, não
é possível autenticar os painéis incorporados
com o Active Directory ou o Cognito ou basicamente
qualquer outra tecnologia de logon único
que você possa estar usando.
Portanto, muitas vezes é possível usar o mesmo mecanismo de autenticação
que você está usando para autenticar o
acesso ao aplicativo no qual está incorporando o painel e usá-lo
para passar a autorização para o próprio QuickSight.
E você precisa colocar na lista de permissões os domínios
em que a incorporação é permitida.
Portanto, no QuickSight, você precisa fornecer uma
lista explícita que diga: "Vou permitir a incorporação
desses nomes de domínio, desses aplicativos".
Dessa forma, pessoas aleatórias na Internet não podem acessar seu painel
e fazer com que você seja cobrado por coisas
que não esperava.
Do ponto de vista da implementação,
mais uma vez, ele tem um SDK JavaScript para incorporar facilmente esses
painéis em qualquer tipo de aplicativo baseado na Web.
E há também uma API que ela oferece se você
quiser acesso de nível inferior
ou se quiser incorporar isso em um aplicativo de nível inferior
que esteja, você sabe, indo para C++ ou algo
assim, certo?
Portanto, há um SDK JavaScript para incorporação rápida em aplicativos
da Web, mas também há uma API que permite fazer isso
em praticamente qualquer contexto que você
possa imaginar.
Portanto, esses são os painéis.
Não há muito o que falar sobre os painéis em si.
É exatamente o que você pensa que seria.
Mas os painéis incorporados têm algumas nuances que
vale a pena conhecer.
Você precisa conhecer o recurso Insights de aprendizado de
máquina do QuickSight.
Esse é um recurso relativamente novo
e está aparecendo cada vez mais no exame.
Há algumas coisas que o QuickSight pode fazer usando
o aprendizado de máquina.
Portanto, insights de aprendizado de máquina, você sabe, é apenas
uma espécie de termo abrangente para alguns desses diferentes
recursos que estão no QuickSight.
Uma delas é a detecção de anomalias com base em ML.
Portanto, ele pode usar o que é chamado de floresta de corte
aleatório, que é um algoritmo proprietário publicado
pela Amazon, do qual eles se orgulham muito.
E pode identificar automaticamente os principais contribuintes
para mudanças significativas em suas métricas.
Assim, ele encontra automaticamente os valores discrepantes para você.
Ele tenta encontrar coisas que são anomalias em seu conjunto de dados
e pode identificar quais são.
Portanto, se você precisar entender
quais são os outliers em seu conjunto
de dados e tentar entender o que
os está causando e gerando, poderá usar a detecção de anomalias
com ML para tentar identificar o que constitui
um outlier automaticamente com base no aprendizado
de máquina.
Ele também pode fazer previsões usando aprendizado de máquina.
É muito importante lembrar disso: a previsão alimentada por ML.
Por baixo do capô, ele também usa seu
algoritmo de floresta de corte aleatório, mas é usado para
detectar sazonalidade e tendências ao longo do tempo.
E a maneira como ele funciona
é excluindo automaticamente os valores discrepantes
usando a floresta de corte aleatório e também pode imputar valores
ausentes.
Assim, ao usar o aprendizado de máquina, ele pode pegar
um conjunto de dados incompleto ou confuso e fazer previsões,
preservando automaticamente as tendências
sazonais e as tendências de longo prazo.
Portanto, é isso que a previsão baseada em ML faz por você.
Outro recurso de insight de aprendizado de máquina são as narrativas automáticas.
Basicamente, ele adiciona o que eles chamam de história de
seus dados aos painéis no QuickSight.
Um exemplo de como isso se parece está aqui no slide.
Portanto, neste exemplo da documentação deles, a receita
total de 17 de novembro de 2018 diminuiu dois
por cento de blá a blá, e a taxa de crescimento composta
dos últimos quatro dias é blá, o que foi pior
do que o esperado.
Portanto, ele apenas permite que você traduza seus
dados para o inglês simples.
E você sabe, às vezes é mais fácil para as pessoas consumirem
isso do que um gráfico ou um visual.
Ele permite que você interprete esses dados
e faça coisas como dizer se esses dados são bons ou ruins
automaticamente usando o aprendizado de máquina.
O QuickSight também tem uma guia de insights em sua interface do usuário,
que fornece o que chamamos de insights sugeridos.
Portanto, se você acessar a guia insights, ela poderá informar quais desses
recursos de aprendizado de máquina podem ser relevantes para
o seu conjunto de dados e fornecer insights sugeridos prontos para uso, para que
você possa examiná-los e incorporá-los à sua análise.
