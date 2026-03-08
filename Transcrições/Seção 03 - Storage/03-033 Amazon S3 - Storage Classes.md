A primeira é a finalidade geral padrão do Amazon S3.
Em seguida, temos o acesso infrequente do Amazon S3.
Depois, temos o acesso pouco frequente de uma zona do Amazon S3.
Em seguida, temos a recuperação instantânea do Glacier, a recuperação flexível do Glacier, o Glacier Deep Archive e,
por fim, a Intelligent-tiering do Amazon S3.
Portanto, aprenderemos sobre todas essas classes em profundidade nesta palestra.
Mas você precisa conhecê-los para o exame.
Então, quando você criar um objeto no Amazon S3, poderá escolher sua classe.
Você também pode modificar sua classe de armazenamento manualmente ou, como veremos, pode usar as configurações de ciclo
de vida do Amazon S3 para mover objetos automaticamente entre todas essas classes de armazenamento.
Então, primeiro, antes de entrarmos nas classes, vamos definir o conceito de durabilidade e disponibilidade.
Portanto, a durabilidade representa quantas vezes um objeto será perdido pelo Amazon S3.
Portanto, o Amazon S3 tem uma durabilidade muito alta.
Chama-se 11 nove.
Portanto, nove nove pontos e nove vezes 9%.
E isso significa que, em média, se você armazenar 10 milhões de objetos no Amazon S3.
Você pode esperar perder um único objeto uma vez a cada 10.000 anos, portanto, ele é bastante durável e a durabilidade é a mesma
para todas as classes de armazenamento no Amazon S3.
A disponibilidade representa a prontidão de um serviço e, portanto, depende da classe de armazenamento.
Por exemplo.
O padrão S3 tem um 99. 999% de disponibilidade.
Isso significa que cerca de 53 minutos por ano, o serviço não estará disponível.
Isso significa que você receberá alguns erros ao lidar com o serviço, portanto, é necessário levar
isso em consideração ao desenvolver seus aplicativos.
Então, o padrão S3 tem 99. 999 disponibilidade.
Ele será usado para dados acessados com frequência.
Esse é o tipo de armazenamento que você usa por padrão.
Além disso, ele tem baixa latência e alta taxa de transferência.
Ele pode suportar duas falhas de instalação simultâneas no lado da AWS.
E os casos de uso para ele serão a análise de big data, aplicativos móveis e de jogos, bem como
a distribuição de conteúdo.
Em seguida, temos o acesso infrequente ao S3.
Portanto, esses são dados que serão, como o nome indica, acessados com menos frequência, mas que exigem
acesso rápido quando necessário.
O custo será menor do que o padrão S3, mas você terá um custo de recuperação.
Portanto, o AI padrão do S3 é 99. 9% de disponibilidade.
Portanto, um pouco menos disponível.
E o caso de uso para ele será a recuperação de desastres e os backups.
E o Amazon S3, uma zona de acesso pouco frequente.
Uma zona II tem uma durabilidade muito alta, mas apenas em um único AZ, e os dados serão perdidos se o AZ for destruído de
alguma forma, assim como a disponibilidade, que é ainda menor.
Portanto, é 99. 5% de disponibilidade.
Portanto, os casos de uso do S3 One Zone II são para armazenar cópias secundárias de backups de dados locais
ou dados que você possa recriar.
Em seguida, temos as classes de armazenamento da geleira.
Portanto, Glacier é, como o nome indica, muito frio.
Portanto, é um armazenamento de objetos de baixo custo destinado a arquivamento e backup.
E o preço é que você pagará pelo armazenamento, além de pagar por um custo de recuperação e suas três classes
de armazenamento.
No Glacier, você tem a recuperação instantânea do Amazon S3 Glacier, que oferece recuperação em milissegundos,
o que é ótimo.
Por exemplo, para dados que são acessados uma vez por trimestre e a duração mínima de armazenamento é de 90 dias.
Portanto, trata-se de um backup, mas você precisa acessá-lo em milissegundos.
Depois, temos a recuperação flexível da geleira.
Ele costumava se chamar Amazon S3 Glacier.
Mas depois renomearam as coisas à medida que adicionaram mais níveis.
Portanto, a recuperação flexível do Amazon Glacier tem três flexibilidades.
Portanto, você tem um local rápido para obter os dados de volta entre 1 e 5 minutos.
Você tem o padrão de obter os dados de volta entre 3 e 5 horas ou em massa, que é gratuito, onde
você obtém os dados de volta entre 5 e 12 horas.
E a duração mínima do armazenamento também é de 90 dias.
Portanto, aqui, instância significa que você recupera os dados instantaneamente, e flexível significa que você está disposto
a esperar até, por exemplo, 12 horas para recuperar seus dados.
Além disso, temos o Glacier Deep Archive, que se destina ao armazenamento de longo prazo.
Portanto, também temos dois níveis de recuperação.
Temos um padrão de 12 horas e um padrão de 48 horas.
Portanto, você pode estar pronto para esperar muito tempo para recuperar dados, mas isso lhe proporcionará o menor custo.
Além disso, a duração mínima do armazenamento é de 180 dias.
Portanto, como você sabe, são muitas classes de armazenamento.
E há menos uma chamada S3 Intelligent-tiering, que permitirá que você mova objetos entre as camadas
de acesso com base nos padrões de uso.
E, para isso, você incorrerá em uma pequena taxa de monitoramento mensal e em uma taxa de classificação automática.
E não há taxas de recuperação na classificação inteligente S3.
Portanto, há o nível de acesso frequente que é automático.
Esse é o padrão aqui.
Em seguida, temos a camada de acesso pouco frequente para objetos não acessados, por exemplo, por 30 dias.
Em seguida, você tem o nível de acesso instantâneo ao arquivo automático também para objetos não acessados por mais de 90 dias.
E o nível de acesso ao arquivo é opcional.
E você pode configurá-lo de 90 dias a sete dias.
Além disso, há a camada de acesso ao deep archive, também opcional, que pode ser configurada para
objetos que não foram acessados entre 100 e 80 dias e mais de 700 dias.
Portanto, a classificação por níveis do S3 serve para que você possa sentar e relaxar enquanto isso.
O S3 move objetos para você.
Portanto, se compararmos todas as classes de armazenamento, você não precisará se lembrar desses números, mas
é apenas para você entender o que eles são.
Assim, você obtém durabilidade de 11 noves em todos os lugares.
Então, a disponibilidade diminui quanto menos zonas você tiver.
É claro que ele apenas mostra a você, por exemplo, a taxa de duração mínima de armazenamento e assim por diante.
Portanto, dedique algum tempo para examinar esse diagrama por conta própria.
Você deve entendê-la, mas não deve se lembrar dela com certeza.
Portanto, se observarmos alguns preços, por exemplo, no Leste dos EUA, esse é o tipo de preço que você teria para
todas as classes de armazenamento.
E, mais uma vez, você não deve se lembrar de tudo, mas é bom dar uma olhada em seu tempo livre para
ter certeza de que entendeu.
Porque se você entender qual é o nome das classes, poderá entender essas classes.
Muito bem, então é isso para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
