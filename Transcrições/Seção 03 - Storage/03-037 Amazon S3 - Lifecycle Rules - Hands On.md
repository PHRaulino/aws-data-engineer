Então, vamos criar
uma regra de ciclo de vida para nossos buckets.
Essa regra será chamada de regra de demonstração, e a aplicaremos
a todos os objetos nos compartimentos, e eu a reconheço.
Portanto, podemos ver que temos cinco ações de regras diferentes.
Podemos mover versões atuais de objetos entre
classes de armazenamento, versões
não atuais de objetos entre classes, versões atuais de
objetos expiradas, excluir permanentemente
versões não atuais de objetos e, finalmente, excluir
objetos expirados, excluir marcadores ou upload incompleto de
várias partes.
Portanto, cinco casos de uso diferentes.
Vamos dar uma olhada em cada um deles.
Portanto, para mover os objetos da versão atual entre as classes
de armazenamento, isso significa que você
tem um bucket de versão, e a versão atual é a versão mais recente
exibida para o usuário.
Assim, por exemplo, podemos fazer
a transição para a AI padrão após 30 dias.
Então, podemos passar para a camada inteligente após 60 dias.
Então, podemos entrar
na geleira depois de 90 dias para uma recuperação instantânea.
Depois de 180 dias, a recuperação flexível e, talvez,
o arquivamento profundo após 365 dias.
Portanto, você pode fazer uma transição o quanto quiser.
Está bem?
E precisamos retomar isso para reconhecer o que fazemos.
Também podemos, por exemplo,
mover versões não atuais com mais rapidez.
Portanto, neste caso, queremos mover um objeto que
não é atual, ou seja, um objeto que foi substituído,
entre aspas, por um objeto próximo.
Portanto, podemos dizer que, ok,
queremos mover este aqui para a geleira flexível porque sabemos
que, após 90 dias, não precisaremos dele para recuperação.
Portanto, isso é perfeito e está tudo pronto, mas
poderíamos adicionar mais transições.
E, por exemplo,
queremos expirar as versões atuais dos objetos após, e na parte
inferior você pode configurá-lo após 700 dias.
O mesmo vale para as opções não circulantes.
Também queremos excluí-los permanentemente após 700 dias.
Ok, então isso é algo que podemos fazer e agora podemos
dar uma olhada em todas essas
transições e ações de expiração.
Isso é bom porque mostra uma linha do tempo do
que vai acontecer com a versão atual
e as versões não atuais dos objetos.
Portanto, se estivermos satisfeitos com tudo isso,
podemos ir em frente e criar essa função, e ela
atuará em segundo plano para fazer o que deve ser feito.
Então é isso.
Agora você sabe como automatizar a movimentação de objetos
no AWS Free entre diferentes classes de origem.
Espero que tenham gostado e nos veremos na próxima palestra.
