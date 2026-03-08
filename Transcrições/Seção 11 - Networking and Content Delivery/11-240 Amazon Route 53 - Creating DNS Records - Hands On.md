Então,
agora vamos criar nossos primeiros registros no Route 53.
Então, vou para a minha zona hospedada
e, nela, vou criar alguns registros simples.
Então, vamos dar uma olhada.
Vamos criar um registro clicando aqui.
E, aqui, posso ter apenas um nome de registro.
Mas você pode inserir o que quiser aqui.
É assim que você criaria seus nomes de domínio.
Agora é preciso especificar o tipo de registro.
Portanto, você pode ver que há muitos tipos de registros aqui, mas, por
enquanto, vamos mantê-los simples.
Vamos mantê-lo como um registro A.
E que consiste em rotear um endereço IPv4 em
um nome de domínio para um endereço IPv4.
Portanto, a resposta será o
valor 1, 1, ponto, 2, 2, ponto, 3, 3, ponto, quatro, quatro.
Esse é apenas um valor que queremos ter, e esse
não é um domínio, um IP que possuímos no momento, mas apenas
para mostrar a você um valor aleatório.
Posteriormente, faremos o roteamento para uma instância real do instituto.
Está bem.
TTL é tempo de vida.
Vamos deixar como 300 segundos no momento.
E a política de roteamento
também dará uma olhada nela mais tarde.
Deixaremos tudo como um roteamento simples. Está bem.
Então, vamos em frente e criar esse registro.
E agora meu registro foi criado com sucesso.
Portanto, a ideia é que, se eu for testar. stephanetheteacher. com, ele solicitará
minha zona de host.
Qual é o valor disso? E eles não vão dizer,
bem, o valor disso é 1, 1, ponto, 2, 2, ponto, 3, 3,
ponto, 4, 4.
Portanto, se você tentar fazer isso com um navegador
da Web, se pegar o navegador, abri-lo e pressionar
Enter, ele não mostrará muitas
coisas, porque no momento não temos
11. 22. 33. 44, provavelmente
não existe nenhum servidor com esse IP também.
E se eu tentar acessar apenas esse URL, ele não
funcionará. Está bem.
Portanto, o que sabemos é o que está acontecendo nos bastidores.
Portanto, para isso, vamos digitar algumas linhas de comando.
Agora, você pode usar a linha
de comando no laptop com Windows ou no Mac, mas,
como quero que todos sigam o mesmo caminho que eu, vou
mostrar como fazer isso usando
os ambientes CloudTrail no AWS.
Então, vou abrir o console de gerenciamento
e clicar aqui para abrir o shell da nuvem, que me permitirá executar
alguns comandos usando uma interface de linha de comando padrão
do Linux. Está bem.
Mas não há problema
se você quiser fazer isso com seu próprio terminal no
Windows ou no Mac.
Está bem. Portanto, meu terminal não está pronto.
E se você estiver no Windows, o
comando de pesquisa NS funcionará. Se você estiver no Mac,
o comando dig também funcionará.
Mas, como você pode ver, esses comandos não são
encontrados no meu shell de nuvem.
Portanto, preciso que você os instale.
Então, eu faço o sudo yum e, em seguida,
instalo o minus Y e, depois,
o bind minus utils.
E ele instalará a pesquisa de VNS
e os comandos dig em meu shell de nuvem.
Portanto, vamos limpar a tela.
E agora vamos tentar fazer uma pesquisa
de NS, teste. stephanietheteacher. com.
E, como você pode ver, obtive uma resposta,
que está no teste. stephanietheteacher. com, está indo para
11. 22. 33. 44, que
corresponde ao que está acontecendo aqui, o que
é legal.
Apresentei o comando dig um pouco mais porque
estou mais familiarizado
com ele, mas se você digitar dig e depois o URL que
você tem, tudo bem.
E pressione Enter,
você verá isso e terá os comandos errados.
Então, stefantheteacher. com, então vamos
limpar essa tela e redigitar os comentários.
Está bem.
Bem, aqui, vamos
ver que temos a seção de respostas
e diz, teste. stephanetheteacher. com é um registro a, e este é
o valor do registro. Por isso, gosto mais dela,
porque mostra o TTL, como veremos mais adiante,
e também mostra o registro, o fato de que não é
um registro. Está bem.
Assim, criamos nosso primeiro registro de rota 53 e
conseguimos consultá-lo usando um terminal,
o que é legal.
Obviamente, carregá-lo em uma página da Web não funciona no momento,
mas veremos como fazer isso mais tarde, quando tivermos
um servidor real.
Portanto, espero que tenham
gostado desta palestra e nos vemos na próxima.
