Então, apenas uma
Portanto, por padrão,
agora todos os buckets estão tendo uma criptografia padrão de SSE-S3.
Portanto, ele é aplicado automaticamente
a novos objetos em direção aos novos compartimentos.
Mas você pode alterar
isso para uma criptografia padrão diferente, por exemplo, SSE-KMS.
No entanto, você também pode forçar a criptografia
usando uma política de bucket para recusar qualquer chamada de API para
colocar um objeto S3 sem os cabeçalhos de criptografia corretos.
Assim, por exemplo, SSC-KMS ou SSE-C.
Portanto, esse é o tipo de políticas de balde que você poderia
ter, por exemplo, esta está
dizendo: "ei, se você fizer um objeto PUT, mas
não tiver o cabeçalho de criptografia que diz AWS KMS, negue essa solicitação".
Ou, ei, se você estiver fazendo upload disso,
mas não houver algoritmo do lado do cliente, ou seja, não houver SSE-C, negue
esse objeto.
Portanto, este é apenas um
exemplo, mas pelo menos você vê que uma política
de bucket também pode forçar uma maneira de ter criptografia em seus buckets.
E, a propósito, as políticas de bucket sempre
serão avaliadas antes das configurações de criptografia padrão.
Então é isso, lembre-se de que a criptografia
padrão está ativada por padrão com o SSC-S3, mas você pode alterá-la
e pode aplicar uma política de bucket preventivamente
para forçar a criptografia que você deseja.
Muito bem, é isso.
Espero que tenham gostado e nos veremos na próxima palestra.
