Então, agora vamos falar sobre
Porque já vimos como criar
um site, mas seria bom poder atualizá-lo de forma segura.
Assim, você pode versionar seus arquivos no Amazon S3,
e essa é uma configuração que deve
ser ativada no nível do bucket.
Portanto, temos meu bucket e ele está habilitado com controle de versão.
Assim, sempre que um usuário fizer
upload de um arquivo, ele criará uma versão desse arquivo
na chave selecionada.
E, se fizermos o upload novamente da mesma
chave, se substituirmos esse arquivo,
ele criará uma versão dois, uma versão
três e assim por diante.
Portanto, é uma prática recomendada versionar seus buckets.
Por quê?
Bem, a primeira coisa é que ele protege
contra exclusões não intencionais.
Assim, por exemplo, se você excluir uma versão de arquivo,
na verdade, você apenas adiciona um marcador
de exclusão e, portanto, pode restaurar versões
que estavam lá anteriormente.
Você também pode reverter facilmente para uma versão anterior.
Portanto, se quiser voltar ao que aconteceu há dois dias,
você pode pegar um arquivo e revertê-lo.
Portanto, há algumas observações das quais você precisa estar ciente.
Em primeiro lugar, qualquer arquivo que não tenha sido
versionado antes da ativação do controle de versão terá a versão nula.
E também que, se você suspender o controle de versão,
ele não excluirá a versão anterior,
portanto, é uma operação segura.
Agora, vamos entrar no console
e ver como podemos usar o controle de versão.
