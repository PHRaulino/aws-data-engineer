Agora, felizmente, graças ao hands on, esperamos que você saiba exatamente quais são as diferenças.
Na minha opinião, isso é bastante óbvio, mas nunca é demais examinar um exemplo e ver o que acontece.
Portanto, o CloudWatch é para métricas de desempenho, métricas, CPU e rede e para criar painéis de controle.
Você também pode receber eventos e alertas.
E, por fim, temos uma ferramenta de agregação e análise de registros, se quisermos.
Então, acho que todos nós já conhecemos bem o CloudWatch.
O CloudTrail pode ser novo para você, mas basicamente serve para registrar as chamadas de API feitas em sua conta
por todos e por tudo, e você pode definir algumas trilhas para recursos específicos para obter mais informações
apenas sobre o EC2.
E é um serviço global.
Agora, finalmente, a configuração serve para registrar as alterações de configuração e avaliar a configuração dos recursos em relação às regras
de conformidade.
Finalmente, você terá uma linha do tempo das alterações em conformidade com essa interface de usuário agradável.
Portanto, acho que são serviços bem distintos e não creio que haja confusão.
Mas vamos analisar um balanceador de carga elástico para ver como cada um desses serviços pode ajudá-lo a entender o que está
acontecendo com seu ELB.
Assim, o CloudWatch pode monitorar o número de conexões de entrada, pode visualizar o número de códigos de erro como
uma porcentagem de um tempo e talvez possamos ter um painel para ter uma ideia do desempenho do balanceador de carga.
Talvez possamos até mesmo transformá-lo em um painel global se você tiver vários balanceadores de carga para um aplicativo global.
Agora, configure por que usaríamos a configuração no Elba?
Bem, talvez queiramos rastrear as regras do grupo de segurança para o balanceador de carga, garantindo que ninguém
faça nada suspeito ou altere nada.
Talvez queiramos mudar.
Acompanhe também as alterações de configuração do próprio balanceador de carga para ver se alguém modifica os
certificados SSL ou.
ET cetera, et cetera.
Talvez também tenhamos uma regra para dizer que sempre deve haver um certificado SSL atribuído ao balanceador
de carga.
E talvez nunca devêssemos permitir o tráfego não criptografado no balanceador de carga.
Isso poderia ser duas regras de conformidade diferentes que você configurou.
Por fim, o CloudTrail rastreará quem fez alterações no balanceador de carga com chamadas de API.
Portanto, caso alguém altere as regras do grupo de segurança, ou alguém altere o certificado SSL ou o remova,
ou qualquer outra coisa, o CloudTrail será a forma de sabermos quem fez essas alterações.
Portanto, todas essas ferramentas são bastante complementares quando você pensa nisso, e quando você entende como
elas são usadas para o balanceador de carga, que eu acho que é um ótimo exemplo, então você vai arrasar.
Alguma dúvida?
Quanto a você no exame.
Espero que isso faça sentido e vejo vocês na próxima palestra.
