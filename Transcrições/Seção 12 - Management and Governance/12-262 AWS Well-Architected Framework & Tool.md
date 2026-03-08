há uma estrutura chamada AWS Well-Architected Framework.
E vou descrevê-lo para você.
Essa é uma ferramenta e uma estrutura
que permite que você crie bons aplicativos no AWS.
Portanto, é uma leitura bastante longa
e, por isso, tentarei resumi-la para você em alguns slides.
Portanto, a ideia é que, com uma estrutura bem arquitetada, uma
vez que você implemente as práticas recomendadas,
você vá para os resultados, e eu
lhe darei as principais diretrizes.
A primeira é que, para parar de adivinhar sua necessidade de capacidade,
use grupos de dimensionamento automático e assim por diante.
Testar sistemas em escala de produção.
Assim, com o AWS, você pode executar rapidamente grandes testes em grandes
infraestruturas e encerrá-los uma hora depois.
Portanto, não há motivo para não testar
em escala de produção.
Também automatize o que lhe permite facilitar
a experimentação arquitetônica.
Se você tiver um modelo de formação
de nuvem, poderá implantá-lo
facilmente em vários ambientes para experimentos.
Você também pode permitir arquiteturas evolutivas.
Portanto, sua arquitetura pode mostrar ao longo
do tempo que pode começar, por exemplo, com instâncias EC2 e
um load bouncer e evoluir para uma arquitetura mais sem servidor,
como API Gateway e Lambda.
Portanto, projete com base nessas mudanças de requisitos e assim por diante.
Além disso, impulsione a arquitetura usando dados.
Portanto, os dados são muito importantes.
Você precisa movê-lo pelo armazenamento e assim por diante.
E, por fim, melhorar nos dias de jogo.
A ideia é que você experimente sua boa produção
arquitetônica, experimente-a e veja como pode melhorar.
Portanto, você precisa enviar sua solicitação,
por exemplo, para os dias de venda relâmpago que colocam muita pressão
em sua arquitetura.
Portanto, a estrutura da arquitetura é composta por seis pilares.
A primeira é a excelência operacional.
A segunda é a segurança.
A terceira é a confiabilidade.
O quarto é a eficiência do desempenho.
Quinto, otimização de custos.
E seis um, sustentabilidade.
Portanto, você precisa conhecer todos eles, quero
dizer, apenas os nomes, certo?
Não é o que eles representam,
mas os nomes são bem explícitos
e você pode acessar o site para saber mais sobre eles,
mas esse não é o foco deste curso.
Portanto, esses pilares não são algo a ser equilibrado
ou trocado, eles são, na verdade, uma sinergia.
Por exemplo, se você melhorar sua excelência operacional,
provavelmente melhorará também sua otimização de custos.
E se você for mais sustentável, provavelmente
também terá uma maior eficiência
de desempenho e assim por diante.
Portanto, para ajudar a guiá-lo por essa estrutura,
existe uma ferramenta chamada AWS Well-Architected.
E é uma ferramenta de estrutura para analisar suas arquiteturas em relação
aos seis pilares que acabei de definir.
E então você adapta as práticas recomendadas de arquitetura.
Portanto, é assim que você se parece
e veremos isso em um segundo.
Então, como isso funciona?
Bem, você seleciona sua carga de
trabalho e depois responde às perguntas.
Você analisa suas respostas
em relação aos seis pilares que acabei de definir.
E então você obtém aconselhamento.
Você recebe vídeos, relatórios de documentação
e vê os resultados em um painel.
Então, vamos dar uma olhada para ver como essa ferramenta funciona.
Então, aqui estou eu na interface do usuário da ferramenta bem arquitetada
e vou definir uma carga de trabalho.
Assim, você pode, por exemplo, definir uma carga de trabalho de demonstração
e dizer que esse é o seu aplicativo de produção.
Você pode dizer que este é o meu aplicativo prod.
Ok, o proprietário da avaliação será John@example. com.
Estamos em produção e funcionando em
duas das regiões que escolherei.
Portanto, este e o US-West-2 são perfeitos.
Podemos especificar regiões que não sejam do AWS, IDs de contas e assim por diante.
E você pode simplesmente especificar
muitas informações sobre sua infraestrutura e arquitetura.
Em seguida, vou aplicar as lentes.
E essas lentes são o tipo de perguntas que você aplica
à sua arquitetura.
Portanto, aplicaremos a lente da estrutura bem arquitetada.
Mas você tem a lente FTR, a lente sem servidor, a lente SaaS
e pode até mesmo criar suas lentes personalizadas,
se quiser.
Mas, por enquanto, manteremos a
simplicidade e responderemos apenas a perguntas
sobre a estrutura bem arquitetada.
Portanto, vamos definir a carga de trabalho.
E, uma vez que você tenha isso, precisa começar a revisar.
Portanto, começaremos a analisar e, em seguida, analisaremos
as lentes do AWS Well-Architected Framework.
Então, aqui eu tenho alguns recursos no lado direito
que posso fechar.
A ideia é que você tenha
muitas perguntas sobre os seis pilares, por exemplo,
11 perguntas sobre excelência operacional e 10 perguntas sobre
segurança, seis sobre sustentabilidade, e as coisas podem mudar com
o tempo, é claro, mas a ideia é que você responda
às perguntas e receba recomendações.
Então, por exemplo, como você determina quais
são suas prioridades?
E diremos, ok, avaliamos os requisitos de governança, as necessidades
dos clientes externos e as compensações.
E, em seguida, responda a uma pergunta.
E então, como você estrutura sua organização?
Talvez eu tenha apenas esta resposta e depois a próxima.
Portanto, você pode responder a perguntas nos
vários pilares e deve responder a todas
elas em todos os pilares, mas vamos
responder a uma também em eficiência de desempenho, aleatoriamente e a seguir.
Assim, depois de responder a talvez três perguntas,
é claro que há muito mais, você salva e continua.
E aqui, como você pode ver, temos três riscos altos.
Portanto, você pode clicar nessa
lente bem aqui e obterá uma visão geral dela,
bem como os riscos.
Portanto, você pode clicar no próprio risco e ir para
o plano de aprimoramento.
Vemos que temos três de alto risco e zero de médio risco
e, portanto, este era de alto risco, e
aqui estão as recomendações relativas a esse risco.
Portanto, preciso avaliar as necessidades dos clientes internos, avaliar
o cenário de ameaças e assim por diante.
E, se eu clicar nele, obtenho a seção na própria
estrutura que me diz exatamente o que preciso fazer.
Portanto, isso é muito importante.
Depois, voltarei a responder a mais perguntas e me certificarei
de que isso seja abordado.
Portanto, essa ferramenta apenas fornece feedback.
E, com o tempo, você pode definir marcos.
Você pode examinar seus planos de aprimoramento e assim por diante.
E a ideia é que, quando você tiver certeza de que essa estrutura
funciona para você, seu aplicativo
estará pronto para produção e sua carga
de trabalho estará em conformidade e bem arquitetada, certo?
Isso é tudo para essa ferramenta.
Espero que tenham gostado
e nos veremos na próxima palestra.
