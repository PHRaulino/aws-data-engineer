É um armazenamento seguro para sua configuração e seus segredos.
E, opcionalmente, você pode optar por criptografar essas configurações e, portanto, torná-las secretas
usando o armazenamento de parâmetros de serviço sem servidor.
Ele é dimensionável, durável e o SDK é muito fácil de usar sobre ele.
Se você atualizar seus parâmetros, terá um rastreamento de versão deles.
A segurança é fornecida pelo IAM e você recebe notificações com o Amazon EventBridge.
Em alguns casos, você tem integração total com o CloudFormation.
Isso significa que o CloudFormation pode aproveitar os parâmetros do armazenamento de parâmetros como parâmetros
de entrada para suas pilhas.
Então, vamos dar um exemplo.
Temos um aplicativo e, em seguida, temos o armazenamento de parâmetros SSM.
Portanto, podemos armazenar a configuração de texto simples dessa forma.
Em seguida, as permissões de IAM de seus aplicativos serão verificadas.
Por exemplo, sua função de instância do EC2.
Ou você pode ter uma configuração criptografada.
Nesse caso, o armazenamento de parâmetros vai criptografá-lo com o KMS.
Portanto, o serviço será usado para criptografia e descriptografia.
E, é claro, você precisa garantir que o seu aplicativo tenha acesso à chave KMS subjacente para executar
a criptografia e a descriptografia.
Portanto, você pode armazenar parâmetros no armazenamento de parâmetros com uma hierarquia.
Assim, por exemplo, você pode definir meu departamento como um caminho.
E abaixo do my app e depois do dev.
Em seguida, temos o banco de dados de desenvolvimento e a senha do banco de dados dentro dessa pasta.
Isso significa que seus parâmetros vão até o final da hierarquia.
Podemos subir um nível e armazenar um parâmetro para a url do banco de dados de produção, bem como uma senha do banco de dados de produção, e subir para outro
aplicativo ou outro departamento que realmente permita que você organize seus parâmetros da maneira que
desejar, de forma estruturada.
E isso simplificará suas políticas de IAM, permitindo que os aplicativos tenham acesso a um departamento inteiro,
a um aplicativo inteiro ou apenas a um caminho específico do ambiente do departamento de aplicativos.
Você também tem a oportunidade de acessar o Secrets of Secrets Manager por meio da loja Parameter, usando esta
referência aqui.
Portanto, trata-se de um pequeno truque que poucas pessoas conhecem.
Por exemplo, se você quiser encontrar o Ami mais recente para o Amazon Linux
Two em sua região específica, isso é algo que está disponível no armazenamento
de parâmetros como uma chamada de API.
Portanto, se pegarmos um aplicativo, por exemplo, nossa função lambda de desenvolvimento terá uma função IAM que
permite acessar o URL do banco de dados e a senha do banco de dados no desenvolvimento do meu aplicativo.
E, se você tiver uma função lambda prod, graças a uma política IAM diferente e talvez algumas variáveis
de ambiente, poderá acessar a url do banco de dados prod e a senha do banco de dados prod de outro caminho.
Agora, no Gerenciador de sistemas, você tem dois tipos de níveis de parâmetros.
Você tem o nível padrão e o nível avançado.
Portanto, a grande diferença será em relação ao tamanho.
Portanto, quatro kilobytes versus oito kilobytes.
E também a disponibilidade de uma política de parâmetros para o padrão um que não temos.
Mas, para os avançados, temos alguns.
O tipo avançado de parâmetros será de US$ 0. 05 por mês, enquanto o primeiro será gratuito.
Então, quais são essas políticas de parâmetros.
E isso é apenas para parâmetros avançados.
Bem, isso permite que você atribua um tempo de vida a um parâmetro.
Isso significa uma data de validade para forçar os usuários a atualizar ou excluir dados confidenciais, como senhas.
E você pode atribuir várias políticas ao mesmo tempo.
Portanto, aqui está um exemplo de política.
Portanto, essa é uma política de expiração para excluir um parâmetro.
E você diz: ei, nesse registro de data e hora, você deve excluir esse parâmetro.
E, por meio da integração do EventBridge, o EventBridge receberá notificações sobre isso.
Portanto, neste exemplo, 15 dias antes de o parâmetro expirar, você receberá uma notificação no EventBridge,
o que nos dá tempo suficiente para realmente atualizá-lo e garantir que o parâmetro não seja excluído
por causa do TTL.
Ou talvez, às vezes, você queira garantir que os parâmetros sejam alterados de vez em quando, de modo que possa
ter uma notificação de não alteração no EventBridge, de modo que, se um parâmetro não for atualizado por 20 dias,
você também será notificado.
Portanto, você pode ser muito criativo com o armazenamento de parâmetros, mas agora você entendeu a ideia por trás disso.
Portanto, espero que tenham gostado desta palestra e nos vemos na próxima.
