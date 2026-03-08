é hora de proteger esses usuários em grupos
para que não sejam comprometidos.
Portanto, para isso, temos dois mecanismos de defesa.
A primeira é definir o que
chamamos de política de senha.
Por quê?
Bem, porque quanto mais forte for a senha que
você usar, maior será a segurança de suas contas.
Portanto, no AWS, você pode configurar uma política
de senha com diferentes opções.
A primeira é que você pode definir um tamanho
mínimo de senha e pode exigir
tipos específicos de caracteres.
Por exemplo, você pode
querer ter uma letra maiúscula, uma letra minúscula, um número,
caracteres não alfanuméricos, por exemplo, um ponto
de interrogação e assim por diante.
Em seguida, você pode permitir ou não que os
usuários do IAM alterem suas próprias senhas,
ou pode exigir que os usuários alterem suas
senhas depois de algum tempo para que a senha expire,
por exemplo, para dizer que a cada 90 dias os usuários
devem alterar suas senhas.
Por fim, você também pode impedir a reutilização
de senhas para que os usuários, quando
mudarem suas senhas,
não a mudem para a que já têm ou para
a que tinham antes.
Portanto, isso é ótimo.
Uma política de senha é realmente útil contra
ataques de força bruta em sua conta.
Mas há um segundo mecanismo de defesa que
você precisa conhecer ao fazer o exame.
E essa é a autenticação multifator ou MFA.
É possível que você já o tenha usado em
alguns sites, mas no AWS ele é obrigatório
e é muito recomendável usá-lo.
Portanto, os usuários têm acesso à sua conta e podem fazer
muitas coisas, especialmente se
forem administradores.
Eles podem alterar a configuração,
excluir recursos e outras coisas.
Portanto, é absolutamente necessário
proteger pelo menos a sua conta raiz e, com sorte, todos
os seus usuários IAM.
Então, como podemos protegê-los além da senha?
Bem, você usa um dispositivo MFA.
Então, o que é MFA?
A MFA usa a combinação de uma senha que você conhece
e um dispositivo de segurança que você possui.
E essas duas coisas juntas têm uma
segurança muito maior do que
apenas uma senha.
Por exemplo, vamos considerar a Alice.
Alice sabe sua senha, mas
também tem um token de geração de MFA.
E ao usar essas coisas juntas durante
o login, ela conseguirá fazer
um login bem-sucedido no MFA.
Portanto, o benefício da MFA é que, mesmo que Alice tenha
perdido sua senha por ter sido roubada
ou hackeada, a conta não será
comprometida porque o hacker também
precisará obter o dispositivo físico de Alice,
que pode ser seu telefone, por exemplo, para fazer um login.
Obviamente, isso é muito menos provável.
Então, quais são as opções de dispositivos MFA na AWS?
E você precisa conhecê-las para fazer o exame,
mas não se preocupe, elas são bem simples.
O primeiro é um dispositivo MFA virtual.
É isso que usaremos na prática.
Assim, você pode usar o Google Authenticator,
que funciona apenas em um telefone de cada vez,
ou usar o Authy.
Portanto, para o Authy, você tem suporte
para vários tokens em um único dispositivo.
Isso significa que, com o dispositivo MFA virtual,
você pode ter sua conta raiz, seu
usuário IAM, outra conta, outro usuário IAM.
Depende de você.
Você pode ter quantos
usuários e contas quiser em seu dispositivo
MFA virtual, o que o torna uma solução muito fácil de usar.
Agora temos outra
coisa chamada Universal 2nd Factor
ou U2F Security Key, que é um dispositivo
físico.
Por exemplo, uma YubiKey da Yubico
e a Yubico é um terceiro para a AWS.
Não é a AWS que fornece isso.
Trata-se de um terceiro.
E usamos um dispositivo físico porque
talvez seja muito fácil,
você o coloca em seus chaveiros
e pronto.
Portanto, esse YubiKey oferece suporte a vários usuários
raiz e IAM usando uma única chave de segurança.
Portanto, você não precisa de tantas chaves quanto
usuários, caso contrário, haverá um pesadelo.
Então você tem outras opções.
Você tem um dispositivo MFA de chaveiro de
hardware, por exemplo, este fornecido
pela Gemalto, que também é um terceiro da AWS.
E, por fim, se estiver usando a nuvem do governo
nos EUA, a AWS GovCloud, você terá um chaveiro especial
parecido com este, fornecido pela
SurePassID, que também é um terceiro.
Então é isso.
Já vimos a teoria sobre
como proteger sua conta, mas vamos
implementar isso na próxima
aula.
Então, vejo você na próxima palestra.
