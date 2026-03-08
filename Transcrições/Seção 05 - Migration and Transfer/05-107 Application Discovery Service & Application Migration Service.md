Portanto, há dois casos de uso quando
Por exemplo, você quer começar
do zero e aproveitar a nuvem diretamente.
Nesse caso, você não precisa fazer uma migração.
Mas se você tiver servidores e data centers locais
e quiser migrar para a nuvem, precisará
planejar sua migração.
E uma maneira de fazer isso é planejar a migração
usando o AWS Application Discovery Service.
Portanto, a ideia é que você examine seus servidores e colete
informações sobre os dados de utilização
do servidor e o mapeamento de dependências, que serão importantes
para suas migrações, para que possamos
entender como migrar e o que migrar primeiro.
Portanto, há dois tipos de migração que você pode fazer.
Um deles é chamado de Descoberta sem agente usando um conector.
E isso lhe dá informações sobre suas máquinas virtuais,
sua configuração, seu histórico de desempenho,
como uso de CPU, memória e disco.
Ou você pode executar um agente para
fazer um Application Discovery Agent, e isso
lhe dá mais atualizações e mais informações
de dentro de suas máquinas virtuais.
Por exemplo, a configuração do sistema, o desempenho,
os processos em execução e os detalhes de todas
as conexões de rede entre seus sistemas,
o que é bom para obter o mapeamento de dependências.
Agora, todos esses dados de resultados podem
ser visualizados em outro serviço chamado AWS Migration Hub.
Portanto, esse Application Discovery
Service realmente o ajuda a mapear o que você precisa mover
e como eles estão interconectados.
Mas então você realmente precisa se mover.
E a maneira mais simples de migrar do local
para o AWS é usar o Serviço de migração de aplicativos do AWS, também
chamado de MGN.
Portanto, isso costumava ser chamado de CloudEndure
Migration, mas agora foi substituído.
E a ideia é que, usando o Serviço de
Migração de Aplicativos da AWS, ou seja, o MGN, você pode
fazer a rehospedagem, também chamada de solução lift-and-shift,
na qual você converte seu serviço físico, virtual
ou outro serviço em outras nuvens para ser executado nativamente na AWS.
Como isso funciona?
Bem, digamos que você tenha um data center corporativo
com aplicativos de sistema operacional e bancos de dados, e eles são executados em discos.
O que acontecerá é que você executará
o Serviço de migração de aplicativos.
E o agente de replicação que você
precisa instalar no data center executará
uma replicação contínua dos discos para que você tenha, por
exemplo, instâncias EC2 de baixo custo e volumes EBS
que recebam essa replicação de dados.
Agora, no dia em que estiver pronto para realizar um corte,
você poderá realmente passar da fase de preparação para a produção
e ter uma instância maior do EC2 do tamanho desejado, bem como volumes
EBS que correspondam ao desempenho necessário.
Portanto, a ideia é que você replique os dados
e, em algum momento, faça um corte.
E essa é, de longe, a maneira mais simples de fazer isso.
Portanto, ele oferece suporte a uma ampla variedade de plataformas,
sistemas operacionais e bancos de dados.
E isso proporciona um tempo de inatividade mínimo,
além de custos reduzidos porque,
bem, você não precisa contratar engenheiros complexos para fazer
isso.
Isso é feito automaticamente por esse serviço.
Então é isso.
Espero que você tenha gostado.
E eu o verei na próxima palestra.
