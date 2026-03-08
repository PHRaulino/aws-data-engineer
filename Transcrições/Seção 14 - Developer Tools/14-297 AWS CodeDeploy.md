falar sobre o CodeDeploys.
Portanto, o CodeDeploys também
é uma maneira de implantarmos nosso aplicativo automaticamente.
Agora, a diferença é que o CodeDeploy é um pouco mais permissivo.
Não é necessário usar o Beanstalk ou o CloudFormation.
Isso é totalmente independente.
Portanto, com o CodeDeploy,
temos nosso aplicativo,
que está na versão um, e queremos
que você o atualize para a versão dois.
Portanto, o CodeDeploy encontrará uma maneira de fazermos isso.
Portanto, o CodeDeploy trabalha com duas coisas.
Ele funciona com instâncias do EC2.
Assim, você pode ter muitas instâncias do EC2 sendo
atualizadas de V1 para V2, mas isso
também funciona com servidores locais.
Portanto, se você tiver servidores no
local e quiser ajudá-los a fazer upgrade da versão
um para a versão dois de seus aplicativos,
é possível fazer isso com o CodeDeploy.
Portanto, o CodeDeploy, se você
observar, é o que chamamos de serviço
híbrido, pois funciona tanto para instâncias locais
quanto para instâncias EC2.
Portanto, o CodeDeploy realmente permite que você trabalhe
com qualquer tipo de servidor, mas você
deve provisionar os servidores com antecedência.
Tudo bem, depende de você.
E você deve configurá-los
para instalar o agente do CodeDeploy
que o ajudará a fazer essas atualizações.
Portanto, o CodeDeploy é um serviço bastante útil no AWS.
Ele realmente permite que as pessoas façam
a transição do On-Premises para o AWS usando a mesma maneira de
implementar o aplicativo
com seus servidores On-Premise
ou suas instâncias EC2.
Como se trata de um serviço
avançado, não posso fazer uma demonstração
para você, mas o que você precisa lembrar é que
ele permite atualizar as instâncias e os aplicativos
do EC2 e os aplicativos dos servidores locais da versão um para a versão
dois, automaticamente, a partir
de uma única interface.
Espero que tenha sido útil.
E eu o verei na próxima palestra.
