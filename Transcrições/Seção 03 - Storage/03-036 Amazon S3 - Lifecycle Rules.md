Então, agora
vamos falar sobre como podemos mover
para que você possa fazer a transição
deles, e este é um diagrama de como isso é possível.
Portanto, como você
pode ver, é possível ir do Standard, por exemplo,
para o Standard IA, para o Intelligent Tiering, para o One-Zone IA e, em seguida, do One-Zone
IA, como você pode ver, é possível ir
para o Flexible Retrieval ou Deep Archive.
Assim, todos os tipos de
permutações são mostrados nesse gráfico.
Portanto, se você sabe que seus
objetos serão acessados com pouca frequência,
mova-os para a AI padrão.
E se você sabe que vai arquivar objetos,
mova-os para a camada
Glacier ou para a camada Deep Archive.
Agora, é claro que a movimentação desses objetos pode ser feita
manualmente, mas podemos automatizar isso usando regras de ciclo de vida.
Portanto, essas regras de ciclo de vida são compostas de vários elementos.
A primeira coisa é uma ação de transição para configurar
o objeto para fazer a transição
para outra classe de armazenamento.
Por exemplo, você pode mudar
para a classe Standard IA após 60 dias depois das criações
ou mudar para o Glacier para arquivamento após seis meses.
Você também pode configurar ações de expiração.
Portanto, configure os objetos para serem excluídos
e expirarem após algum tempo.
Por exemplo, seus arquivos de registro
de acesso devem ser excluídos após 365 dias.
Ou você pode, por exemplo, usar
uma ação de expiração para excluir versões antigas de arquivos
se tiver ativado o controle de versão.
Ou podemos usar isso para excluir uploads incompletos de várias partes
se, por exemplo, os uploads de várias partes tiverem
mais de duas semanas porque, bem, a coisa
já deveria ter sido totalmente carregada.
As regras também podem ser especificadas para um determinado prefixo.
Portanto, eles podem ser aplicados
a baldes inteiros ou a um caminho específico em seus baldes.
E você também pode especificá-lo para tags de objeto específicas.
Portanto, se você quiser criar uma regra apenas
para o departamento financeiro, é possível.
Então, aqui estão alguns cenários.
Por exemplo, você tem um aplicativo no EC2 e ele cria
imagens, miniaturas depois que as
fotos de perfil são carregadas no Amazon S3.
Mas essas miniaturas podem ser facilmente
recriadas a partir da foto
original e só precisam ser mantidas por 60 dias.
Mas as imagens de origem devem poder ser
recuperadas imediatamente durante esses 60
dias e, depois disso, o usuário pode esperar até seis horas.
Então, como você projetaria isso?
Isso é o que uma pergunta de exame lhe perguntará.
Portanto, as imagens de origem do S3 podem estar na classe Standard com
uma configuração de ciclo de vida para fazer a transição para
o Glacier após 60 dias e as imagens em miniatura, portanto, é assim que você
usaria um prefixo para diferenciar entre origem
e miniaturas, por exemplo.
Portanto, as miniaturas podem estar na AI do One-Zone
porque, bem, elas são acessadas com pouca
frequência e podem ser recriadas facilmente, e você pode
ter uma configuração de ciclo de vida para expirá-las
ou excluí-las após 60 dias.
Em outro cenário, uma regra
em sua empresa determina que você
deve poder recuperar imediatamente objetos S3 excluídos por 30 dias, embora
isso possa acontecer raramente.
Após esse período, por até 365 dias, os objetos excluídos
devem poder ser recuperados em 48 horas.
Para isso, podemos ativar o controle de versão do S3 para manter e
ter versões de objetos, de modo que os objetos excluídos sejam
de fato ocultos por um marcador de exclusão
e possam ser recuperados.
Em seguida, você criará uma regra para fazer a transição
das versões não atuais dos objetos para a AI padrão.
Ou seja, as versões que
não são as de nível superior e, depois,
a transição dessas versões não atuais para o Glacier
Deep Archive para fins de arquivamento.
Por fim, como determinamos qual é o número ideal de
dias para fazer a transição de um objeto de uma classe para outra?
Bem, você pode fazer isso graças ao Amazon S3 Analytics.
Portanto, ele lhe dará recomendações para
o padrão e para o padrão IA.
Ele não funciona com o One-Zone IA ou o Glacier.
Assim, os buckets
do S3 terão o S3 Analytics executado sobre eles.
E isso criará um relatório CSV que lhe
dará algumas recomendações e estatísticas.
O relatório será atualizado diariamente
e pode levar de 24 a 48 horas para que a análise
dos dados comece a ser feita.
Portanto, esse é um bom primeiro passo, esse relatório
CSV, para criar regras de ciclo de vida que façam sentido
ou para aprimorá-las.
Muito bem, então é isso para esta palestra.
Espero que tenham gostado e nos veremos na próxima palestra.
