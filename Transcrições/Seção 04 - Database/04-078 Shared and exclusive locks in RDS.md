Um aspecto que quero destacar explicitamente
Isso é algo que aparece no guia do exame, portanto,
é melhor falarmos sobre isso.
Uma maneira de fazer isso é usar o comando Lock.
Então, a ideia dos bloqueios é impedir que duas pessoas
façam a mesma coisa ao
mesmo tempo em algo, certo?
E, como resultado, obtendo resultados conflitantes.
Portanto, implicitamente, os bancos de dados relacionais bloquearão suas tabelas
para evitar que isso aconteça.
Portanto, você não quer que duas pessoas escrevam ao mesmo
tempo na mesma parte dos dados, certo?
E você também não quer que as pessoas leiam os
dados enquanto a gravação estiver em andamento nesse bit de dados.
Portanto, em geral, para garantir a conformidade com a acidez, os bancos de dados bloqueiam
automaticamente e implicitamente
as coisas para evitar que esse tipo de coisa
aconteça.
Você realmente não precisa fazer nada de especial em relação a isso.
No entanto, é possível bloquear explicitamente tabelas ou linhas
para garantir sua própria integridade de dados e controle de simultaneidade,
se você não quiser simplesmente
confiar que o banco de dados fará
a coisa certa.
Pode haver algumas circunstâncias especiais
em que você queira um controle mais explícito sobre esses bloqueios.
Portanto, há dois tipos de travas.
Há o que chamamos de bloqueio compartilhado e bloqueio exclusivo.
Portanto, a sintaxe para um bloqueio compartilhado é For Share.
Veremos um exemplo disso no próximo slide.
Mas um bloqueio compartilhado permite leituras, mas impede gravações.
E pode ser mantido por várias transações.
Portanto, se quiser permitir que as pessoas leiam os
dados que estão sendo acessados pela sua transação,
mas impedir que as pessoas escrevam
neles durante a transação, você
pode dizer For Share para impor um bloqueio compartilhado.
Você também pode ter um bloqueio exclusivo que impede todas
as leituras e gravações em um recurso.
E somente uma transação pode manter
um bloqueio exclusivo por vez.
É por isso que ele é chamado de Exclusivo.
A sintaxe para isso é For Update.
E isso diz: "Enquanto eu estiver acessando esses dados, ninguém poderá lê-los,
ninguém poderá escrever neles, ninguém poderá olhar
ou tocá-los, exceto eu. Alguns exemplos, e esses
são no MySQL, a sintaxe novamente varia de banco de dados
para banco de dados, portanto, não se prenda
muito à sintaxe, mas se você quiser
bloquear uma tabela inteira, poderá dizer Lock Tables,
employees, em que employees é o nome da tabela
que quero bloquear.
Certo, isso bloquearia toda a tabela do funcionário
contra gravação.
E quando terminar,
terei que dizer Unlock Table para liberar o bloqueio.
Agora, o Redshift também tem um comando Lock que funciona
de forma muito semelhante para a mesma finalidade.
Portanto, se eu quiser ter certeza de que ninguém
poderá escrever na minha tabela enquanto eu estiver fazendo alguma coisa, as tabelas de
bloqueio são a maneira de fazer isso.
E você sabe, pensando em termos
do que o exame pode estar perguntando, provavelmente
é sobre isso que eles vão perguntar.
Não sei, na verdade ainda não fiz o exame quando
estou gravando isso,
porque é antes do exame Beta agora.
Portanto, não estou transmitindo conhecimento proibido.
Sou apenas um palpite educado.
Também um exemplo de como fazer um bloqueio compartilhado.
Então, digamos que eu queira permitir
leituras, mas impedir gravações durante essa transação.
Portanto, não estou explicitamente bloqueando e desbloqueando aqui.
Esses bloqueios compartilhados e exclusivos se aplicam apenas
à transação em que estou.
Portanto, enquanto essa instrução select estiver sendo executada,
porque estou dizendo For Share, isso significa
que, durante essa execução, outros processos
podem fazer leituras da tabela, mas ninguém pode escrever nela
enquanto estiver sendo executada.
E, para completar, para o Update, aqui como exemplo de um bloqueio
exclusivo, durante o tempo de
vida dessa transação, ninguém
pode ler ou gravar até que a transação seja concluída.
Portanto, é importante garantir que todas as transações
que tenham um bloqueio sejam concluídas, certo?
Portanto, se por algum motivo essa transação for interrompida
ou não for concluída, você
pode acabar com o que chamamos de deadlock, em que esse
bloqueio nunca é liberado.
Portanto, esse é um modo de falha em potencial e, novamente,
talvez seja algo que o exame espere que você saiba.
