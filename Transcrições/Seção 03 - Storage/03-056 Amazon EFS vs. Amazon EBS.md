Agora, vamos falar sobre
Portanto, os volumes do EBS são anexados a uma instância
por vez, exceto no caso extremo de usar o
recurso de vários anexos
dos tipos de volume io1 e io2, mas isso é para casos
de uso muito específicos.
Os volumes EBS também são bloqueados no nível da AZ, portanto,
aqui está um exemplo.
Temos um EC2 na AZ 1 e temos um
volume EBS anexado a ele, e ele não pode
ser anexado a uma instância do EC2 na AZ 2.
Para o tipo de volume gp2,
o IO aumentará se o tamanho do disco aumentar,
e para os tipos de volumes gp3 e IO1, você pode aumentar
o IO independentemente do tamanho do disco.
Para migrar um volume do EBS entre AZs, precisamos tirar
um instantâneo, para que
ele vá para os instantâneos do EBS e, em seguida,
possamos restaurar o instantâneo em outra AZ.
É assim que passamos de um AZ para o outro.
Agora, os backups dos volumes EBS usarão IO e, portanto, você não deve executá-los
enquanto o aplicativo estiver lidando
com muito tráfego, pois isso
pode afetar o desempenho.
Para suas instâncias do EC2, os volumes EBS de rota de suas instâncias
serão encerrados por padrão se a instância do EC2 for
encerrada, mas você pode desativar esse
comportamento.
Já no caso do EFS, a situação é um pouco diferente.
Portanto, trata-se de um sistema de arquivos
de rede, e o objetivo é realmente anexá-lo a centenas
de instâncias em toda a zona de disponibilidade, de modo que realmente
vemos a distinção aqui.
Assim, com um sistema de arquivos EFS, podemos ter diferentes
alvos de montagem em diferentes AZs e, em seguida,
várias instâncias podem compartilhar esse único
sistema de arquivos.
Portanto, é muito útil, por exemplo, quando você tem
o WordPress e ele é apenas para instâncias
do Linux porque está usando o sistema POSIX.
O EFS tem um preço mais alto do que o EBS, mas você pode aproveitar
as camadas de armazenamento para economizar custos.
Esperamos que você tenha entendido a diferença entre
o EFS e o EBS e, no caso do armazenamento da instância,
ele está fisicamente conectado à instância do EC2 e, portanto,
se você perder a instância do EC2, também perderá
o armazenamento.
Muito bem, é isso, espero que tenham gostado
e nos vemos na próxima palestra.
