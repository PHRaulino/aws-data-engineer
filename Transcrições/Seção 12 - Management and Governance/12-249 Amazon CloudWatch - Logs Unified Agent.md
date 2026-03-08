EC2, bem como métricas, e colocá-los no CloudWatch.
Portanto, por padrão, nenhum registro é enviado do CloudWatch para a sua instância EC2.
Para isso, é necessário criar e iniciar um agente, que é um pequeno programa em suas instâncias do EC2 que enviará os arquivos
de registro que você deseja.
Portanto, a ideia é que suas instâncias EC2 tenham o agente de registros do CloudWatch, por exemplo, em execução, enviando os registros para
os registros do CloudWatch.
Para que isso funcione, sua instância EC2 deve ter uma função IAM que permita enviar o registro para os registros do CloudWatch.
Isso faz sentido, e é bom saber que esse agente de registro do CloudWatch também pode ser configurado em servidores locais, portanto,
é possível ter seus serviços em servidores virtuais, como o VMware, no local, e instalar exatamente o mesmo agente,
que é um pequeno programa Linux, e seus registros também acabarão nos registros do CloudWatch.
Agora, há dois agentes diferentes que você pode encontrar no CloudWatch.
Você tem o agente de logs do CloudWatch, que é o mais antigo, e o agente do CloudWatch Unified, que é
o mais recente.
Portanto, há ambos para servidores virtuais, instâncias EC2, servidores locais etc.
O agente de logs do CloudWatch é a versão antiga e só pode enviar logs para os logs do CloudWatch, enquanto
o agente unificado coletará métricas adicionais no nível do sistema, como processos Ram.
Mostrarei isso no próximo slide e também enviarei os logs para os logs do CloudWatch.
Agora está unificado.
Ele é melhor porque pode fazer tanto métricas quanto registros, daí o nome Unified Agent.
Mas você também pode configurar esse agente com muita facilidade usando o armazenamento de parâmetros do SSM, que é um recurso
que o agente anterior não tinha.
Assim, você pode fazer uma configuração centralizada para todos os seus agentes unificados.
Assim, o agente unificado do CloudWatch pode enviar registros e registros do CloudWatch.
Mas vamos dar uma olhada nas métricas.
Portanto, se você instalá-lo em suas instâncias EC2 ou em seus servidores Linux, poderá coletar métricas.
E quais são eles?
Bem, podemos coletar as métricas da CPU, mas em um nível muito mais granular.
Assim, por exemplo, o usuário do sistema ocioso convidado ativo rouba.
Você não precisa conhecê-los.
Estou apenas lhe dando a granularidade de todas essas métricas.
As métricas de disco são gratuitas.
Use o total de E/S do disco em termos de número de gravações, leituras, bytes, IOPs, Ram, portanto, livre no uso ativo do cache total
netstat, portanto, número de conexões TCP e UDP, bytes de pacotes líquidos.
Você obtém algumas informações sobre os processos.
Portanto, no número total de processos, quantos estão mortos, bloqueados, ociosos, em execução, dormindo, e o espaço varrido, que é uma parte da memória
que está sendo derramada no disco.
Então, quanto é o uso gratuito e a porcentagem de uso.
Portanto, não se lembre, apenas faça uma captura de tela mental desses itens.
O resultado final é que o agente unificado do CloudWatch permite que você obtenha muito mais métricas e detalhes
muito mais granulares do que o monitoramento normal das instâncias do EC2.
Como lembrete, no EC2, você obtém algumas informações sobre disco, CPU e rede, mas não sobre memória
nem swap.
Mas tudo isso em um nível alto.
Se você quiser mais granularidade, pense nos agentes unificados do CloudWatch.
Ok, então é isso para mim.
Espero que tenham gostado e nos veremos na próxima palestra.
