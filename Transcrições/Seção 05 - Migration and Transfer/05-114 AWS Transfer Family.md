Portanto, a ideia é que você queira enviar dados
para dentro e para fora do Amazon S3 ou EFS, mas
não queira usar as APIs do S3.
Você não deseja usar o sistema de arquivos de rede EFS.
Você só quer usar o protocolo FTP.
Nesse caso, você precisa
usar o serviço de transferência de família da AWS.
Portanto, ele suporta três tipos de protocolos.
Ele oferece suporte à transferência da AWS para FTP.
Portanto, o protocolo de transferência de arquivos, FTP.
FTPS, que é o protocolo de transferência de arquivos por SSL, de forma
criptografada.
Ou SFTP, que é um protocolo seguro de transferência de arquivos.
Agora você não quer ser um especialista nisso.
Saiba que o FTP não é criptografado,
enquanto o FTPS e o SFTP são criptografados durante o voo.
Agora, a ideia é que, usando o protocolo
FTP, você possa fazer upload para o S3 ou EFS.
A família de transferência é uma infraestrutura totalmente gerenciada.
Ele é dimensionável, confiável e altamente disponível.
Portanto, você gerencia toda essa capacidade.
E em termos de preço, você pagará por pontos
finais de provisão por hora, além de uma taxa por gigabytes de dados transferidos
para dentro e para fora da família de transferência.
Você pode armazenar e gerenciar as credenciais de um usuário
para esse serviço dentro do serviço.
Ou você também pode se integrar
ao sistema de autenticação existente,
como o Microsoft Active Directory,
LDAP, Okta, Amazon Cognito ou qualquer fonte personalizada.
O uso disso é, obviamente, para ter uma interface
FTP no Amazon S3 ou EFS.
Assim, para compartilhar arquivos, conjuntos
de dados públicos, CRM, ERP, etc., etc.
Portanto, apenas o diagrama para você entender.
A família de transferência tem três versões
e os usuários podem acessar diretamente usando os
pontos finais do FTP ou, opcionalmente, usar um GNS chamado route 53 para fornecer
seu próprio nome de host ao serviço de FTP.
E, em seguida, o serviço de FTP, portanto, a transferência
para o serviço de FTP terá uma função de IAM que será assumida
para enviar ou ler os arquivos do Amazon
S3 ou do Amazon EFS.
E isso é feito de forma transparente.
Você não precisa configurar muitas coisas.
E, por fim, se você
quiser proteger os serviços da família de transferência,
poderá autenticar seus usuários usando
um sistema de autenticação externo, como Active
Directory, LDAP ou tudo o que acabei de dizer
no slide anterior.
Está bem.
Então, digamos que você saiba
que esse recurso é de alto nível, espero que tenha gostado.
e eu o verei na próxima palestra.
