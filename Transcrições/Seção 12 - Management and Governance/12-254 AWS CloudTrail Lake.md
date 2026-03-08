Lake, que é um lago de dados gerenciado para eventos de trilha na nuvem.
Portanto, ele se encarregará automaticamente de armazenar
todos os dados de trilha da nuvem no S3 em algum lugar e
de integrar a coleta, o armazenamento, a preparação e a otimização
de todos esses dados para análises
e consultas subsequentes.
Ele faz isso convertendo todos os
eventos no formato ORC, que é um formato de coluna
de dados que torna mais rápida e eficiente a pesquisa
em um ambiente de data lake quando suas consultas estão
interessadas apenas em determinadas colunas,
o que geralmente é o caso.
Isso permite que você consulte os dados do CloudTrail usando apenas o sql,
o que é muito legal, e veremos
um exemplo disso em alguns slides.
Mas esse é o ponto principal. Ao colocar todos esses
dados de trilha da nuvem em um lago de dados, podemos
consultá-los da mesma forma que
um lago de dados e facilitar a extração de insights de todos esses
dados de trilha da nuvem para ativá-los.
Tudo o que você precisa fazer é clicar na opção de
menu criar armazenamento de dados de eventos no console
quando estiver configurando o Cloud Trail
e verá uma tela como esta à direita.
Por padrão, o período de retenção de dados é de até sete anos.
Depois de fazer isso, você terá mais algumas opções a fazer.
Você precisa especificar os tipos de eventos que deseja rastrear.
É possível especificar eventos de gerenciamento de registro
ou eventos de dados.
Portanto, se não estiver interessado em registrar e pagar
pelo armazenamento e indexação
de todas as operações de recursos, é melhor deixar os eventos
de dados desativados.
Se tudo o que lhe interessa é controlar quem está fazendo o
quê em seus serviços e você
só quer eventos de gerenciamento, no entanto,
dentro dos eventos de gerenciamento,
isso também inclui eventos KMS, e esses eventos KMS podem
se acumular muito rapidamente, porque você atinge
muito o KMSA sempre que faz alguma coisa, se é
que alguma coisa é segura, se você está
usando o KMS.
Isso pode fazer com que seus custos aumentem muito rapidamente.
Portanto, lembre-se de que o CloudTrail pode gerar muitos
dados e você deve ser exigente quanto aos tipos de
dados que está armazenando no Cloud Trail Lake para
manter os custos sob controle, certo?
Portanto, se você não precisa, se não se importa com todas as
solicitações de KMS, não ative essa opção.
Excluir eventos KMS, que está desativado por padrão.
Você verá que, por um bom motivo, os seletores
de eventos básicos podem ser selecionados na interface do usuário.
Você pode dizer, veja aqui, que também podemos escolher eventos da API
de dados do RDS e coisas do gênero.
Mas se você precisar de um controle mais refinado sobre o que
está sendo coletado, poderá
fazer isso com o que chamamos de seletores de eventos avançados,
o que pode ajudá-lo ainda mais a controlar os custos de
armazenamento e o tipo de dados que está sendo ingerido.
Você também pode criar o que chamamos de canais
com o Cloud Trail Lake.
Isso permite que você se integre a eventos que
estão fora do AWS mesmo.
Portanto, se você também quiser consultar coisas que estão acontecendo fora
do AWS como parte disso, poderá fazer isso.
Ele foi desenvolvido para oferecer suporte ao Okta Launch Darkly Lumio e a outros
parceiros do CloudTrail.
Tenho certeza de que essa lista mudará com o tempo,
portanto, não esperaria ser questionado sobre isso.
Exatamente. Você também pode configurar sua própria integração personalizada.
Portanto, se você quiser criar um canal para
seus próprios dados em sua própria fonte proprietária, isso
também é possível.
Voltando aos seletores de eventos avançados, vamos
dar uma olhada em um exemplo de um deles.
Portanto, se eu quiser, por exemplo, registrar todos os eventos de gerenciamento,
mas também quiser registrar -: Não todos
os eventos de recursos, mas apenas colocar e excluir
chamadas de objetos em um prefixo de bucket específico.
Aqui está um exemplo de como você configuraria isso.
Portanto, a parte superior diz que terei um campo de categoria de
evento igual a gerenciamento.
Portanto, é como marcar a caixa de seleção de gerenciamento
na interface do usuário que vimos no console e que diz "Quero
registrar todos os eventos de gerenciamento",
mas, em vez de dizer "Quero registrar todos os eventos de recursos",
vou dizer "não", na verdade, tudo o que quero é essa coisa muito específica
em que quero registrar eventos de colocação e exclusão
de objetos para dois prefixos S3.
Portanto, nos seletores de campo aqui,
estamos dizendo que a categoria do evento deve ser dados.
O tipo de recurso precisa ser um objeto do AWS S3.
O nome do evento precisa ser objeto colocado ou objeto excluído.
E os recursos que um RN precisa começar
com o prefixo de barra do meu balde
ou com o prefixo de barra dois do meu balde.
Portanto, em vez de apenas habilitar toda
a categoria de eventos de dados, estamos dizendo não,
queremos esse subconjunto muito específico dos meus eventos de dados.
E, novamente, essa é uma ferramenta importante
para controlar sua ingestão e seus custos
de armazenamento ao usar o Cloud Trail
Lake.
Porque, novamente, se você não for cuidadoso, isso pode se acumular rapidamente.
Depois de ter todos esses dados, o que você faz com eles?
Bem, ele tem uma pequena interface de usuário para fazer consultas
usando sql, e também tem algo chamado Lake Dashboards para
permitir que você visualize esses eventos.
Porém, de forma mais avançada, você pode implementar suas próprias consultas
SQL, como estamos vendo aqui à direita.
Portanto, há vários exemplos de consultas que
eles fornecem para você começar.
Portanto, você não precisa necessariamente escrevê-los
do zero para coisas comuns que queira fazer.
Um exemplo aqui é à direita,
onde estamos selecionando o horário do evento, a identidade
do usuário e a região de algum armazenamento de dados que temos aqui, e estamos
restringindo isso a um intervalo específico de horários de eventos
e a regiões específicas.
E estamos procurando especificamente por eventos de login no console.
Portanto, isso me fornecerá um relatório de todos
que fizeram login no console do AWS a partir
dessa conta durante esses períodos.
E lembre-se de que uma prática recomendada
para otimizar o desempenho dessas consultas
é vinculá-las ao tempo do evento para restringir
o tempo de execução e os custos.
Portanto, mais uma vez, pode haver muitos dados aqui
e, se você acabar digitalizando todos os seus
dados por engano, porque não restringiu isso por tempo de
evento, poderá acabar executando uma consulta muito cara, não apenas
em termos de tempo, mas também em termos de dinheiro.
Portanto, isso pode ser algo que eles esperam que você saiba.
Como posso controlar meus custos ao consultar o CloudTrail Lake?
Lembre-se sempre de restringir isso ao horário do evento.
