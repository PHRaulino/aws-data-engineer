Q Business. Portanto, o Amazon Q
Business é
um assistente Gen-AI totalmente gerenciado
para seus funcionários.
O que isso significa? Bem, temos um
assistente, mas ele se baseia inteiramente
no
conhecimento e nos dados de sua empresa.
Portanto, este é um caso de uso muito
específico em que a Gen-AI é para sua
empresa e é treinada em seus dados
internos.
Então, por exemplo, o que você pode pedir
à
Amazon Q Business? Bem, você pode dizer:
"Escreva um
anúncio de emprego para uma função de
gerente de
produto sênior", onde temos, é claro, essa
função sendo
muito relevante para o que nossa empresa
está fazendo,
ou "Crie um post de mídia social com menos
de 50 palavras para anunciar a nova
função".
Ou, por exemplo, "O que foi discutido
durante a
reunião da equipe na semana do dia 4/12?"
Portanto, é claro que tudo isso não pode
ser respondido por um modelo de base
geral.
Ele precisa ser um modelo que tenha
sido treinado em seus próprios dados
internos
com a segurança correta, é claro.
Portanto, como um todo, o Amazon Q
Business pode responder a perguntas,
fornecer resumos,
gerar conteúdo e automatizar tarefas, bem
como
executar ações de rotina, como, por
exemplo,
fazer coisas como enviar solicitação de
folga ou enviar convites para reuniões.
Nos bastidores, o Amazon Q Business é
construído sobre
o Amazon Bedrock, mas temos menos controle
e não
podemos escolher qual é o modelo de base
subjacente.
E, na verdade, o Amazon Q Business é
construído com
base em um modelo de múltiplas fundações
do Amazon Bedrock.
Portanto, esse é um serviço de nível um
pouco
mais alto, voltado para um caso de uso
muito
específico de uso e exposição dos dados
internos da
sua empresa sob a perspectiva do LLM
Gen-AI.
Este é um exemplo: estamos perguntando
qual é
o total anual do limite máximo de despesas
de bolso mencionado no resumo do plano de
saúde? Isso é para a nossa empresa,
estamos
no setor médico e temos um documento da
empresa, um PDF, que tem a resposta exata.
Assim, o Amazon Q Business pode consultar
esse
documento, ver o que ele diz e
nos dar a resposta em nosso bate-papo,
de forma semelhante ao RAG, é claro.
E, é claro, teremos uma seção de fontes
na qual diremos que as fontes deste
documento
são o PDF do plano de saúde, e
você pode clicar nele e encontrá-lo
imediatamente.
Então, vamos dar uma olhada em um diagrama
para entender melhor o Amazon Q Business.
Então, aqui está, primeiro temos alguns
conectores de dados.
Portanto, os conectores de dados são
totalmente gerenciados
pelo RAG, e você pode se conectar a
mais de 40 fontes de dados empresariais
populares.
Portanto, você não precisa aprender sobre
todos
eles, mas é bom ver alguns deles.
Portanto, temos o Amazon S3, onde podemos
armazenar arquivos de dados no AWS,
que é um serviço muito popular.
Temos o Amazon RDS, que é um serviço
de banco de dados, temos o Aurora, outro
serviço de banco de dados, e o WorkDocs,
um serviço usado especificamente para
documentos no AWS.
E depois temos serviços que não são
da AWS, como Microsoft 365, Salesforce,
Google
Drive, Gmail, Slack, SharePoint, etc.,
etc.
E a ideia é que o Amazon Q
Business tenha integrações internas com
esses serviços.
E, depois que a integração for feita,
ele rastreará essas fontes e fará o
que deve ser feito para permitir
que você as pesquise e consulte.
Em seguida, temos também os plug-ins.
Portanto, antes, os conectores de dados se
referiam à
recuperação de dados e à compreensão do
conhecimento interno
de nossa empresa, mas, em seguida, temos
os plug-ins.
E os plug-ins permitem que o Amazon Q
Business realmente interaja com serviços
de terceiros.
Por exemplo, temos Jira, ServiceNow,
Zendesk, Salesforce, etc., etc.
E a ideia é que, por exemplo, se dissermos
ao Amazon Q Business: "Ei, crie um
problema
no Jira", ou seja, crie um tíquete para
que possamos rastrear um problema em nossa
empresa,
o Amazon Q Business aproveitará o plug-in
e
criará automaticamente esse problema no
Jira para nós.
Portanto, além de ler dados, o Amazon
Q Business também tem a capacidade de
criar e mover dados em sua empresa.
E você pode estendê-lo porque pode criar
plug-ins personalizados para
se conectar a qualquer aplicativo de
terceiros usando APIs.
Agora, como acessamos o Amazon Q Business?
Bem, nossos usuários serão autenticados
por meio
de algo chamado IAM Identity Center.
Portanto, o IAM Identity Center é uma
maneira de
os usuários fazerem login, e veremos como,
e depois
que o usuário estiver conectado, ele terá
acesso
apenas aos documentos aos quais deve ter
acesso.
Portanto, ao usar todos os dados da sua
empresa
com o Amazon Q Business, você ainda tem a
certeza de que alguém com menos
privilégios não
poderá acessar todos os seus documentos,
caso contrário,
isso seria, obviamente, um grande risco de
segurança.
Aqui temos o IAM Identity Center, e
nossos usuários farão login nele apenas
com uma caixa de login na
qual você digita um nome de
usuário e uma senha e pronto.
E então você tem o que é chamado de
usuário
autenticado com suas próprias permissões,
porque o IAM Identity Center
sabe o que o usuário pode acessar ou não.
Em seguida, o usuário pode fazer perguntas
ao
Amazon Q Business, que é um aplicativo da
Web, e, é claro, acessar apenas os
documentos aos quais ele deve ter acesso.
Além disso, você pode integrar o IAM
Identity Center com
o que chamamos de provedores de identidade
externa ou IDP.
E pode ser, por exemplo, um login do
Google ou
um Active Directory da Microsoft e assim
por diante.
Isso significa que, em vez de fazer login
e obter uma página de login baseada na
AWS, você fará login em um sistema
em que os usuários já foram criados.
Por exemplo, pode ser seu diretório ativo,
no
qual você tem seu login da Microsoft, ou
pode ser seu login do Google, por exemplo,
se você estiver usando o tipo de espaço
de trabalho do G Suite para sua empresa.
Portanto, isso é muito útil e
realmente anda de mãos dadas com
qualquer sistema de segurança que
você tenha em sua empresa.
Em seguida, temos os controles de
administração.
Portanto, esses são controles usados para
personalizar as respostas
com base no que a sua organização precisa.
Portanto, os controles administrativos são
praticamente a mesma
coisa que os Guardrails no Amazon Bedrock.
Assim, por exemplo, se tivermos um tópico
bloqueado,
como consoles de jogos, e nosso
funcionário perguntar:
"Ei, como posso configurar um Nintendo
Switch novinho
em folha?" Então, você usará o Amazon Q
Business para dizer: "Bem, esse é um
tópico
restrito". Assim, podemos bloquear
palavras ou tópicos específicos,
e também podemos escolher que o Amazon
Q responda apenas com informações internas
em
vez de usar também o conhecimento externo.
Portanto, se especificarmos que ele usará
apenas informações
internas, somente os documentos de sua
empresa
serão usados para responder a uma
consulta.
Caso contrário, teremos acesso ao
conhecimento
mais amplo do modelo de fundação.
Você também pode configurar esses
controles administrativos no controle
global, no nível global, ou seja, para
todos os
tipos de tópicos e todos os tipos de
assuntos.
Ou você pode configurar alguns mais
especificamente em um
nível de tópico para ter controles
administrativos mais
específicos, mas eles são os mesmos,
apenas em
que nível você deseja aplicá-los? Então é
isso
para o Amazon Q Business, espero que você
tenha gostado e nos vemos na próxima
palestra.
