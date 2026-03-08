Vamos falar também sobre o EBS Elastic Volumes.
e não é nada de especial.
Você não precisa habilitar isso explicitamente
se o seu tipo de instância for compatível com isso, o que a maioria faz atualmente.
A ideia por trás do EBS Elastic Volumes é que você não
precisa mais desconectar um volume ou reiniciar
a instância para alterar esse volume.
É um pouco mágico. Eu realmente não sei como isso funciona.
Mas, de alguma forma, eles fizeram com que, se você
quiser alterar o tipo de volume, o tamanho dele ou suas características
de desempenho, tudo o que você precisa fazer é ir para
ações e modificar o volume no console, fazer as alterações e tudo isso
acontecerá sem nenhum tempo de inatividade,
o que é bastante impressionante.
Assim, por exemplo, você poderia aumentar o tamanho do volume
sem realmente reduzir a instância
à qual ele está anexado.
Isso é útil, certo, se você
estiver ficando sem espaço em disco?
Só preciso acrescentar mais alguns. É muito fácil fazer isso.
No entanto, você só pode aumentar o tamanho do
volume, não pode diminuí-lo.
Quer dizer, você pode imaginar como isso causaria alguma complexidade
se você tentasse reduzir um volume que já estivesse
cheio, certo?
Então, sim, isso faz sentido para mim.
Outro aspecto interessante é que você também pode alterar
o tipo de volume em tempo real.
Então, digamos que você queira passar do armazenamento Gp2 para o Gp3.
Você pode realmente fazer isso.
Basta acessar actions/modify volume, alterar o tipo de volume e, enquanto
isso, especificar também o desempenho
desejado de IOPS ou taxa de transferência.
Se você não fizer isso, ele tentará fazer uma
estimativa com base no desempenho máximo de Gp2 ou no desempenho
mínimo de Gp3 que você teria obtido.
Mas é uma prática melhor dizer explicitamente
o que você quer lá.
Mas você pode fazer isso.
Na verdade, você pode alterar o tipo de volume em tempo real, sem
precisar desativar a instância ou desanexar
o volume ou qualquer outra coisa.
Ele simplesmente fará isso. Não sei como.
Mais uma vez, (risos) é um pouco mágico.
Você também pode aumentar ou diminuir
seus atributos de desempenho.
Portanto, se você quiser apenas aumentar o desempenho
de IOPS ou de taxa de transferência, também poderá fazer
isso em tempo real.
Portanto, esse é o EBS Elastic Volumes.
Saiba que essas são coisas que você pode fazer com o EBS
e que são muito legais.
