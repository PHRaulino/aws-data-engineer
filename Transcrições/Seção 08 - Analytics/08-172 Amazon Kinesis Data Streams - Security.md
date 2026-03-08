Portanto, a segurança será uma parte importante de seu exame.
É uma seção dedicada a ela e, portanto, precisamos
saber sobre a segurança de cada tecnologia.
Então, vamos falar (indistintamente) sobre a Kinesis.
Basicamente, controlamos o acesso e as autorizações ao
Kinesis usando políticas de IAM.
E podemos obter criptografia
em voo usando os endpoints HTTPS.
Isso significa que os dados que enviamos
à Kinesis serão criptografados e não poderão ser interceptados.
Também podemos obter criptografia
em repouso nos fluxos do Kinesis usando o KMS.
E se você quiser criptografar sua mensagem no lado do cliente e descriptografá-la
no lado do cliente, deverá fazer isso
manualmente.
Portanto, é possível fazer isso, mas é mais difícil.
Não há clientes para ajudá-lo
a fazer isso, e cabe a você
implementar esse tipo de tecnologia de criptografia.
Por fim, se você quiser acessar o Kinesis em sua VPC dentro de
uma rede privada, poderá
usar algo chamado VPC Endpoints.
Eles são acessíveis para o Kinesis, o que basicamente
permite que você acesse o Kinesis, não na Internet pública,
mas na sua Internet VPC privada.
Então, digamos que para a segurança do Kinesis...
Não se preocupe, no geral, no final do curso, terei uma seção inteira
sobre segurança descrevendo em
detalhes a segurança de cada tecnologia, mas pelo menos
isso lhe dá uma ideia de como funciona
a segurança do Kinesis.
Muito bem, é isso.
Eu o verei na próxima palestra.
