Portanto, o CloudTrail é uma maneira de obter governança, conformidade e auditoria para sua conta da AWS, e o CloudTrail
é ativado por padrão.
Isso permitirá que você obtenha um histórico de todos os eventos e chamadas de API feitas na sua conta
do AWS pelo console, pelo SDK, pela CLI ou por outros serviços no AWS, e todos esses logs serão exibidos no CloudTrail.
Agora, o que você pode fazer é colocar esses logs do CloudTrail nos logs do CloudWatch ou no Amazon
S3 e criar uma trilha a ser aplicada a todas as regiões ou a uma única região, se quiser que ela se acumule.
Todo esse histórico de eventos acumulado em todas as regiões em um bucket específico, por exemplo,
S3.
E quando usamos o CloudTrail, por exemplo, podemos dizer que alguém foi em frente e excluiu algo no AWS.
Por exemplo, digamos que uma instância do EC2 esteja sendo encerrada e você queira descobrir quem fez isso.
Bem, a resposta é dar uma olhada no CloudTrail, porque o CloudTrail terá essa chamada de API e poderemos
chegar ao fundo da questão e entender quem fez o quê e quando.
Portanto, para resumir, o CloudTrail está no meio e as ações do SDK, da CLI ou do console ou até mesmo dos usuários IAM
e das funções IAM ou de outros serviços estarão no console do CloudTrail.
Podemos dar uma olhada nele para inspecionar e auditar o que aconteceu e, se quisermos ter todos os eventos
por mais de 90 dias, podemos enviá-los para os logs do CloudWatch ou para um bucket do S3.
Então, vou me aprofundar um pouco mais no CloudTrail.
Portanto, temos três tipos de eventos que você pode ver no CloudTrail.
O primeiro é chamado de Eventos de gerenciamento.
E isso representa operações que são realizadas em recursos em sua conta do AWS.
Por exemplo, sempre que alguém configurar a segurança, usará a chamada de API chamada IAM attach role policy,
e isso aparecerá no CloudTrail.
Se você criar uma sub-rede, ela também será exibida.
Se você configurar o registro, isso aparecerá por padrão.
Qualquer coisa que modifique seus recursos ou sua conta da AWS aparecerá no CloudTrail e, por padrão, as trilhas são configuradas para
registrar eventos de gerenciamento, não importa o que aconteça.
Você pode separar dois tipos de eventos de gerenciamento.
Você tem os eventos de leitura que não modificam os recursos.
Por exemplo, alguém está listando todos os usuários no IAM ou listando todas as instâncias do EC2 no EC2.
Esse tipo de coisa pode ser separado dos eventos de gravação que podem modificar recursos.
Por exemplo, alguém exclui ou tenta excluir uma tabela do DynamoDB e, obviamente, os eventos de gravação provavelmente
têm muito mais importância porque podem causar danos à sua infraestrutura, enquanto os eventos de leitura são apenas
para obter informações que ainda são muito importantes, mas talvez menos destrutivas.
Depois, há os eventos de dados, que são separados e, por padrão, os eventos de dados não são registrados porque são operações
de alto volume.
Então, o que são eventos de dados.
Bem, você tem uma atividade no nível do objeto do Amazon S3, por exemplo, obter objeto, excluir objeto.
Colocar objeto.
E, como você pode ver, isso pode estar acontecendo muito em um bucket S3.
E é por isso que eles não são registrados por padrão.
E você tem a opção de se separar.
Novamente, eventos de leitura e gravação.
Portanto, um evento de leitura será um objeto get, enquanto um evento de gravação será um objeto delete ou um objeto put.
Outro tipo de evento que você pode ter no CloudTrail são as atividades de execução da função AWS Lambda.
Portanto, sempre que alguém usar a API de invocação, você poderá obter insights sobre quantas vezes suas funções Lambda estão sendo
invocadas.
E, mais uma vez, esses volumes podem ser realmente altos se suas funções lambda forem executadas com frequência.
E o terceiro tipo de evento no CloudTrail é chamado de eventos do CloudTrail Insights.
Por isso, falarei com você sobre os insights do CloudTrail daqui a pouco.
Mais detalhes no próximo slide.
Agora, vamos falar sobre os insights do CloudTrail.
Portanto, quando temos tantos eventos de gerenciamento em todos os tipos de serviços e tantas APIs acontecendo muito, muito
rapidamente em sua conta, pode ser bastante difícil entender o que parece estranho, o que parece incomum e o que
não parece.
E é aí que entram os insights do CloudTrail.
Portanto, com os insights do CloudTrail, que você precisa ativar e pagar, ele analisará seus
eventos e tentará detectar atividades incomuns em sua conta.
Por exemplo, provisionamento impreciso de recursos, atingimento de limites de serviço, explosão de ações, lacunas na atividade de manutenção
periódica.
Portanto, o CloudTrail analisará como são as atividades normais de gerenciamento para criar uma linha de base,
uma linha de base e, em seguida, analisará continuamente qualquer coisa que seja um tipo certo de evento.
Portanto, sempre que algo é alterado ou tentado ser alterado para detectar padrões incomuns.
Portanto, os eventos de gerenciamento serão analisados continuamente pelo CloudTrail Insights,
que gerará eventos de insights caso algo seja detectado.
Assim, essas anomalias e esses eventos de insights aparecerão no console do CloudTrail.
Eles também serão enviados para o Amazon S3, se você desejar.
E um evento EventBridge.
Portanto, no CloudWatch, o evento será gerado caso você precise automatizar esses insights do CloudTrail, por
exemplo, para enviar um e-mail.
Portanto, essa é a ideia por trás dos insights do CloudTrail.
Por fim, vamos falar sobre as retenções de eventos do CloudTrail.
Portanto, por padrão, os eventos são armazenados por 90 dias no CloudTrail e, depois, são excluídos.
Mas, às vezes, você pode querer ter eventos por mais tempo, caso queira voltar a algo que aconteceu
talvez há um ano para fins de auditoria.
Portanto, para manter os eventos além desse período, é necessário registrá-los no S3.
Portanto, envie-os para o S3.
E então você usaria o Athena para analisá-los.
Portanto, de forma muito simples, todos os seus eventos de gerenciamento, eventos de dados e eventos de insights serão armazenados
no CloudTrail por um período de retenção de 90 dias.
Em seguida, você registraria esses dados em seus buckets S3 para retenção de longo prazo.
E quando estiver pronto para analisá-los, você usará o serviço Athena, que é um serviço sem servidor
para consultar dados no S3 para encontrar os eventos nos quais você está interessado e saber mais sobre eles.
Espero que você tenha gostado desta palestra e nos vemos na próxima.
