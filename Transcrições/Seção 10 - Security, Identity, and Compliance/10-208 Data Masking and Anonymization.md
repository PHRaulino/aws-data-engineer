Já abordamos o mascaramento e
vezes neste curso, mas parece que
faz sentido revisitar esse
assunto na seção de segurança.
Novamente, esse é um conceito importante
que o exame espera que você conheça.
Portanto, sempre que estiver lidando com informações
de identificação pessoal ou outros dados confidenciais,
pode ser qualquer coisa.
O mascaramento é uma forma de ofuscar esses dados.
Por exemplo, você já deve ter visto que, na fatura
do seu cartão de crédito, eles ocultam todos os dígitos
do seu número de cartão de crédito, exceto os quatro últimos, apenas para
garantir que, se alguém obtiver uma cópia da fatura, não
poderá fugir com o número completo do seu cartão de crédito.
O mesmo acontece quando você vê seu número de seguro social listado.
Normalmente, você verá
tudo, exceto os últimos quatro dígitos, mascarados.
Você também pode usá-lo para mascarar senhas.
Você sabe que, ao digitar
as senhas, muitas vezes elas são ocultadas ou mascaradas
com estrelas ou o que quer que seja, e há suporte integrado
para mascaramento no Glue Data Brew e no Redshift.
Veja abaixo um exemplo de uma política de mascaramento
que mascararia totalmente um número de cartão de crédito.
Criar política de mascaramento. A propósito, isso é no Redshift.
Mask credit card full é o nome dessa política,
com credit card sendo o campo que contém
o número do cartão de crédito de um tipo V, car 2 56 usando e, em seguida,
a string de máscara.
E vamos dizer que esse será
um texto que entrará nele.
Esse é apenas um exemplo de criação de uma política de mascaramento
para um número de cartão de crédito em um Redshift.
E, novamente, o erro de sintaxe não é algo que se espera
que você saiba, mas saiba que você
pode fazer isso.
Além disso, a anonimização é outra maneira de fazer isso.
Portanto, em vez de mascarar algo, você pode substituir
esses dados por algo que
não possa ser rastreado até sua origem.
Assim, você poderia simplesmente substituir o número do cartão
de crédito ou a senha ou o que quer que seja por informações aleatórias,
poderia embaralhá-las de
modo a embaralhar tudo em uma determinada coluna para
que os números reais do cartão de crédito das pessoas não correspondessem
à pessoa real.
Outra abordagem seria a criptografia, que
pode ser determinística,
em que você sempre pode obter o mesmo resultado ao criptografar
a mesma entrada, ou probabilística, em que você pode
obter um resultado diferente sempre
que criptografar.
O hash é outra técnica sobre a qual também falamos
anteriormente, em que você simplesmente aplica o que chamamos
de função hash à cadeia de caracteres.
E o problema com o hashing
é que você pode obter mais de uma coisa com o mesmo
valor, mas você sabe que, no final, isso apenas
aumenta o anonimato, certo?
Ou, melhor ainda, simplesmente
exclua-o ou não o importe.
Se você não precisar de números de cartão
de crédito ou senhas para o que estiver fazendo, não os pegue.
Se você vir essas informações chegando, exclua-as
durante o ETL ou nem tente importá-las
para começar.
Essa é provavelmente a maneira mais segura de lidar
com informações de identificação pessoal.
Em primeiro lugar, não o tenha.
