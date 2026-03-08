Essa é rápida.
Vamos começar com um princípio de segurança
muito básico, mas importante.
O princípio do menor privilégio e o
guia do exame dizem que você precisa saber o que é isso.
Mas é bem simples. Tudo o que isso significa
é que você está concedendo apenas as permissões necessárias
para que alguém realize uma determinada tarefa.
Portanto, é uma espécie de senso comum, certo?
Não dê às pessoas mais permissões do que elas precisam
para fazer o que precisam fazer.
Caso contrário, eles podem descobrir uma maneira
de explorar ou abusar dessa permissão externa que possuem.
Enquanto estiver desenvolvendo, certamente
faz sentido começar com uma permissão
mais ampla, pois você não sabe exatamente para
o que precisa de permissão quando ainda está criando
um sistema e descobrindo quais componentes
o compõem, certo?
Mas, uma vez terminado, quando você realmente
souber o que alguém precisa fazer com esse
sistema, você deve bloqueá-lo.
Assim que você tiver uma ideia melhor dos serviços
e operações exatos que uma carga de trabalho exige.
Aqui, à direita, temos um exemplo disso.
Portanto, essa é apenas uma política de IAM que restringe o acesso ao S3 para listar
um bucket específico e, além disso, dentro
de um prefixo específico desse bucket.
Portanto, essa metade superior está dizendo que
só permitirei operações de bucket de lista dentro do meu bucket específico
no caminho dos relatórios de dados.
E, para a leitura real dos dados, a única
coisa que permitirei com essa política de IAM é a leitura de arquivos CSV que
estejam sob meu balde específico, barra de dados, barra
de relatórios e terminem com um sufixo CSV.
Portanto, se você tiver, por exemplo, um fluxo de
trabalho que exija que
as pessoas, ou um sistema ou serviço, leiam arquivos CSV de um local específico,
não há motivo para dar a elas
acesso a nada além desse local.
E, além disso, apenas para os tipos específicos de arquivos
que eles podem precisar desse local, certo?
Portanto, esse é um exemplo do princípio do privilégio alugado.
E se você não tiver certeza de quais privilégios
precisa para uma operação, poderá usar uma ferramenta chamada
IAM Access Analyzer, que
gerará automaticamente políticas de privilégios alugados com
base na atividade de acesso realmente observada.
Portanto, se enquanto estiver testando o sistema, você estiver
fazendo apenas o que deve fazer, poderá usar o IAM Access Analyzer
para fornecer automaticamente um ponto de partida de como essas
políticas com menos privilégios podem ser.
