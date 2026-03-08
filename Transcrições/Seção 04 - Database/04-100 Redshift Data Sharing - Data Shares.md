de dados, se você quiser compartilhar dados entre clusters do Redshift,
que permite compartilhar com segurança dados em tempo
real entre clusters do Redshift apenas para fins de leitura, certo?
Portanto, se você quiser publicar seus dados em outros
clusters do Redshift e permitir
que outras pessoas leiam seus dados, essa é uma maneira
muito boa de fazer isso.
Por que você quer fazer isso?
Bem, um deles é o isolamento da carga de trabalho.
Portanto, se você estiver compartilhando seus dados com outro
cluster, se esse outro cluster ficar atolado, isso
não afetará o desempenho do produtor, o cluster principal do
qual você está compartilhando os dados.
Portanto, se você quiser ter certeza de que algum departamento
desonesto da sua organização não pode prejudicar
o desempenho do seu cluster Redshift, talvez você apenas compartilhe
seus dados com o cluster Redshift dele
e, se ele tiver problemas de desempenho,
isso não afetará você.
A colaboração entre grupos
como essa é um caso de uso para isso.
Portanto, se você tiver outro departamento ou outra organização
que precise acessar seus dados de forma lida, essa é uma maneira
de compartilhar esses dados com eles ou com
grupos dentro de uma organização.
E também pode ser usado
não apenas para compartilhar dados entre
grupos, mas também entre ambientes.
Portanto, uma boa aplicação do compartilhamento de dados é o compartilhamento
de dados entre ambientes de desenvolvimento, teste e produção.
Isso me permitiria desenvolver alterações em um
aplicativo ou algo do gênero com base nos mesmos dados
que estão em produção.
Mas, novamente, ter esse isolamento
para que meu tráfego de desenvolvimento e o que
estou fazendo no desenvolvimento
não afetem o que está acontecendo na produção.
Isso pressupõe que o que você está fazendo
pode ser feito com dados somente de leitura, é claro.
Talvez você também queira fazer isso para licenciar o acesso
aos seus dados por meio do AWS Data Exchange.
Portanto, se você quiser publicar
seus dados e basicamente vendê-los a outros usuários do AWS,
o compartilhamento de dados é a forma
de fazer isso com o AWS Data Exchange.
O que você pode compartilhar? Você pode compartilhar bancos de dados inteiros.
É possível compartilhar esquemas,
tabelas, exibições específicas e/ou funções definidas pelo usuário.
Portanto, você tem um controle de acesso refinado sobre
quem pode ver o quê, e pode ser qualquer uma ou todas essas
coisas.
Falei sobre isso anteriormente,
mas o compartilhamento de dados depende de uma arquitetura de produtor e consumidor
em que toda essa segurança refinada é controlada
pelo produtor, a pessoa que publica
esses dados.
Novamente, temos isolamento para que o desempenho
do cluster produtor não seja afetado por
nenhum consumidor desses dados usando o compartilhamento de dados.
No entanto, os dados serão ao vivo e consistentes em termos
de transações, de modo que esses consumidores terão uma visão ao vivo e consistente
em termos de transações do que está acontecendo
no cluster do produtor.
Para que o compartilhamento de
dados funcione, os dois clusters devem
ser criptografados e devem usar tipos de nós RA3.
Se você estiver compartilhando dados entre regiões,
isso poderá envolver cobranças de transferência,
portanto, fique atento à sua fatura nesse caso.
E há três tipos diferentes de compartilhamentos de dados.
Há o Standard, sobre o qual falamos,
apenas um cluster para outro.
Também o AWS Data Exchange, se você quiser compartilhar
dados com o Data Exchange.
E o terceiro tipo de compartilhamento
de dados é gerenciado pelo AWS Lake Formation.
