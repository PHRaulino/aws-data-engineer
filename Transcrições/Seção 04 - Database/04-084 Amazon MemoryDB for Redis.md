Portanto, trata-se de um serviço de banco de dados na memória,
durável e compatível com o Redis.
Portanto, a diferença entre o Redis e o MemoryDB para o Redis
é que, enquanto a intenção do Redis é ser usado como um cache
com alguma durabilidade, o MemoryDB é realmente um banco de dados que
tem uma API compatível com o Redis.
Portanto, ele oferece um desempenho ultrarrápido,
com mais de 160 milhões de solicitações por segundo, ou
seja, um desempenho muito alto e
dados na memória, mas é um armazenamento de dados durável com o
log de transações Multi-AZ.
Portanto, esse é um tipo de funcionamento diferente do Redis.
Ele será dimensionado sem problemas de dezenas de gigabytes
a centenas de terabytes de armazenamento, e
os casos de uso do Memory-DB for Redis serão seus
aplicativos da Web e móveis, jogos on-line,
streaming de mídia e assim por diante.
Portanto, se você tiver muitos microsserviços
e eles precisarem de acesso a um banco de dados na memória
compatível com o Redis, isso é perfeito.
Você usa o MemoryDB para o Redis.
Você terá uma velocidade ultrarrápida na memória,
bem como um log de transações Multi-AZ,
que será armazenado em vários AZs e lhe dará acesso
à recuperação rápida e à durabilidade
dos dados, se necessário.
Ok, apenas uma visão geral, mas
isso deve ser suficiente para o exame.
Espero que tenham gostado e nos veremos na próxima palestra.
