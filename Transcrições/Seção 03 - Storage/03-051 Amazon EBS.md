qual veremos as diferentes opções de armazenamento para instâncias do EC2.
Portanto, primeiro, os mais importantes
serão os volumes EBS.
Portanto, vamos definir o que eles são.
E o volume EBS significa Elastic Block Store.
É uma unidade de rede que você não pode anexar
às instâncias enquanto elas estiverem em execução.
E nós os usamos sem nem mesmo saber.
Portanto, esses volumes EBS nos permitem manter os dados
mesmo depois que a instância é encerrada.
E esse é o objetivo principal.
Podemos recriar uma instância
e montar o mesmo volume EBS de antes, e recuperaremos
nossos dados.
Isso é muito útil.
Portanto, esses volumes EBS no nível do CCP só podem ser montados
em uma instância de cada vez, certo?
E quando você cria um volume EBS, ele é vinculado
a uma zona de disponibilidade específica.
Isso significa que você não pode ter um volume EBS criado,
por exemplo, em us-east 1a anexado a uma
instância em us-east 1b.
Veremos isso no diagrama em um segundo momento.
Então, o que você acha dos volumes do EBS?
Bem, você pode pensar neles como pendrives de rede.
Portanto, é um pendrive USB que pode ser retirado de um computador e colocado
em outro computador, mas que, na
verdade, não é colocado fisicamente em um computador.
É um anexo através da rede.
Agora vamos dar uma olhada nisso.
Portanto, os volumes EBS são unidades de
rede, como eu disse, não são unidades físicas, certo?
Portanto, para se comunicar entre
a instância e o volume do EBS, ele usará a rede.
E como a rede deles é usada, pode
haver um pouco de latência de um computador
para chegar a outro servidor.
Agora, os volumes do EBS, por serem uma unidade de rede,
podem ser desconectados de uma instância
do EC2 e anexados a outra muito rapidamente.
E isso o torna muito útil quando você
deseja fazer failovers, por exemplo.
Os volumes EBS são bloqueados em uma zona de disponibilidade específica.
Isso significa que, como eu disse, se ele for criado na us-east
1a, não poderá ser anexado à us-east 1b.
Mas veremos nesta seção que, se fizermos um snapshot,
poderemos mover um volume de diferentes
zonas de disponibilidade.
E, por fim, é um volume.
Portanto, você precisa provisionar a capacidade com antecedência.
Portanto, você precisa informar com antecedência quantos
gigabytes deseja e o IOPS, que são as operações de IO por segundo.
E você está basicamente definindo
como deseja que o volume do EBS funcione.
Você será cobrado por essa capacidade de provisionamento e poderá
aumentar a capacidade ao longo do tempo se quiser
ter melhor desempenho ou mais tamanho.
Então, como um diagrama, como ele se parece.
Bem, temos o us-east 1a, temos uma instância do EC2
e podemos anexar, por exemplo, um volume EBS
a essa instância do EC2.
Se criarmos outra instância do EC2, como eu disse, um volume
do EBS não poderá ser anexado a duas
instâncias ao mesmo tempo no nível de profissional de nuvem certificado.
Portanto, o que quero dizer é que
essa outra instância do EC2 precisa
ter seu próprio volume EBS anexado a ela, mas
é bem possível que tenhamos dois
volumes EBS anexados a uma instância.
Pense nisso como dois pendrives de rede em uma única máquina.
Isso faz muito sentido.
Agora, os volumes do EBS estão vinculados a uma zona de disponibilidade.
Portanto, como podemos ver, todo esse diagrama
foi feito até agora usando a us-east 1a.
Portanto, se você quiser ter outros volumes EBS em outra AZ,
precisará criá-los separadamente na outra zona de disponibilidade.
Assim, da mesma forma que suas instâncias do EC2 estão vinculadas a
uma AZ, o mesmo ocorre com os volumes EBS.
Por fim, é possível criar volumes EBS e deixá-los desvinculados
que não precisam ser necessariamente
vinculados a uma instância do EC2 que pode ser
vinculada sob demanda, o que
o torna muito, muito avançado.
Por fim, quando criarmos volumes
do EBS por meio de instâncias do EC2, haverá uma coisa chamada exclusão
no atributo de encerramento.
E isso pode aparecer no exame.
Portanto, se você observar
isso, quando criamos um volume EBS no console, quando criamos
uma instância EC2, há a penúltima
coluna chamada delete on
termination.
E, por padrão, ele está marcado para o volume
raiz e não está marcado para um novo volume EBS.
Portanto, isso controla o comportamento do EBS quando uma instância
do EC2 está sendo encerrada.
Portanto, por padrão, como podemos
ver, o volume EBS raiz é excluído juntamente com
a instância que está sendo encerrada.
Portanto, ele está ativado e, por padrão, qualquer
outro volume EBS anexado não é excluído porque está
desativado por padrão.
Mas, obviamente, como podemos ver nesta interface
do usuário, podemos controlar se você deseja ativar ou
desativar a exclusão no encerramento.
Portanto, o caso de uso, certo, seria,
por exemplo, se você quiser preservar o volume raiz quando
uma instância for encerrada, por exemplo,
para salvar alguns dados, poderá desativar
a exclusão no encerramento para o volume
raiz e estará tudo certo.
E isso pode ser um cenário de exame no exame.
Espero que tenham gostado
e nos veremos na próxima palestra.
