Portanto, o SageMaker é um serviço totalmente gerenciado para desenvolvedores
e cientistas de dados criarem modelos de aprendizado
de máquina.
Portanto, todos os serviços que vimos
até agora nesta seção são serviços
gerenciados de aprendizado de máquina
com uma finalidade muito específica,
por exemplo, traduzir algum texto, transcrever
algum áudio, converter texto
em áudio ou analisar partes de um texto, mas o SageMaker é um
serviço de aprendizado de máquina de nível superior em
que os desenvolvedores ou cientistas
de dados da sua organização criam e desenvolvem
modelos de aprendizado de máquina.
Portanto, é muito mais complexo
e muito mais difícil de usar.
Agora, quando você deseja executar esse tipo de processo para criar
um modelo de aprendizado de máquina, é necessário
executar várias etapas que mostrarei
em um segundo, e tudo isso
é bastante difícil de ser feito em um só lugar, além de ser
necessário provisionar alguns servidores para realizar
essas competições e criar esses modelos, o que também pode ser complicado.
É aqui que entra o SageMaker.
Portanto, o SageMaker tentará ajudá-lo em
todo o processo.
Então, vou mostrar o que realmente é o aprendizado de máquina,
e essa é uma versão simplificada. Se você
for um especialista em aprendizado
de máquina, não fique bravo comigo, por favor,
mas digamos que você queira criar um modelo,
ou digamos que eu queira criar um modelo para
prever a pontuação que você obterá no exame de certificação
CLAP practitioner.
Então, como vou fazer isso?
Digamos, por exemplo, que eu seja um desenvolvedor
ou um cientista de dados
e, portanto, vou reunir todos os seus dados a partir do
desempenho real dos meus alunos.
Assim, pedirei a talvez 10.000 alunos que
me forneçam informações sobre quantos anos de experiência em TI eles
têm, quantos anos de experiência
com a AWS eles têm, quanto tempo gastaram no
curso, quantos exames práticos
fizeram etc. etc., portanto, tentarei
coletar o máximo de dados possível e, em seguida,
rotularei os dados.
Isso significa que você precisa dizer quais colunas
correspondem a quê,
e também precisa dar algum tipo de pontuação,
e a pontuação é a pontuação real que alguém obtém
no exame.
Por exemplo, alguém não foi
aprovado, 670, talvez não tenha feito o curso completamente, esse
seria o motivo.
Talvez alguém tenha sido aprovado com
uma nota alta, ou seja, 990, ou talvez alguém com uma nota ainda mais alta, 934, portanto,
cada aluno obterá uma pontuação específica, e meu palpite
é que, com base nos dados que coletei, posso prever qual será
a pontuação.
Portanto, primeiro fiz a rotulagem,
e esse processo de rotulagem pode ser bastante complicado
na prática.
Em seguida, preciso criar um modelo de aprendizado
de máquina, ou seja, como posso prever essas pontuações com
base nos dados históricos.
Então, você cria esse modelo de aprendizado
de máquina e precisa treiná-lo e ajustá-lo.
Portanto, essa é outra parte que, na verdade, é
bastante difícil de fazer, que é como refinar meu modelo
ao longo do tempo para se ajustar melhor aos meus dados e aos meus resultados.
Agora, o SageMaker e tudo isso o ajudarão com a
rotulagem, a criação,
o treinamento e o ajuste,
mas não só.
Agora temos um modelo de aprendizado de máquina
e ele foi criado, está funcionando
plenamente.
Portanto, agora preciso usá-lo.
Portanto, isso é chamado de implementação de modelos de aprendizado de máquina.
Portanto, receberemos novos dados.
Por exemplo, você é o novo aluno e eu vou
fazer uma pesquisa com você
e perguntar: "Quantos
anos de experiência você tem em
TI, com a AWS, quanto tempo você gastou neste curso?"
E, com base nos dados que você acabou de me fornecer,
aplicarei o modelo de
aprendizado de máquina que criei anteriormente.
E então o modelo de aprendizado
de máquina dirá, por exemplo, "ei, ele envia com base nos dados
que você tem, vou prever que esse aluno
será aprovado com uma pontuação de 906".
E todo esse processo de rotulagem,
construção do modelo,
treinamento, ajuste
e aplicação pode ser feito no SageMaker.
Então, é isso para uma introdução rápida, mas
espero que você tenha
gostado e nos vemos na próxima palestra.
