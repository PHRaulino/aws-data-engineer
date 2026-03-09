
## Visão Geral da Seção
A Seção 03 foca nas tecnologias e serviços de armazenamento oferecidos pela AWS. Aqui o curso faz uma transição de tópicos de alto nível em engenharia de dados para um mergulho profundo em serviços específicos da AWS, com grande ênfase no Amazon S3 (e seus diversos recursos) e outras opções de armazenamento como Amazon EBS, Amazon EFS e AWS Backup.

## Conceitos Principais
- Storage no nível de objetos (Amazon S3) e seus diferentes recursos, como versionamento, replicação, classes de armazenamento e notificações.
- Segurança e criptografia no Amazon S3 (Bucket Policies e Access Points, SSE-S3/KMS).
- Tabelas S3 (Apache Iceberg) introduzindo a fundação para Data Lakehouse e o ecossistema moderno da Amazon Analytics.
- Block Storage (Amazon EBS), que fornece volumes anexados diretamente a instâncias EC2.
- File Storage (Amazon EFS), sistema de arquivos de rede (NFS gerenciado) que permite montagem concorrente entre instâncias e zonas.
- AWS Backup para gerenciamento centralizado e automatizado de rotinas de backup entre os serviços da AWS.

## Resumo das Aulas

### [[03-021 Intro- Storage]]
Apresenta a fundamentação da seção: uma visão geral das tecnologias de armazenamento da AWS com foco em componentes essenciais para a Engenharia de Dados.

### [[03-022 [Important] AWS Console UI Update]]
Uma breve observação para o aluno sobre possíveis atualizações na interface de usuário (UI) do console de gerenciamento da AWS.

### [[03-023 Set up an AWS Billing Alarm]]
Orienta a criação de alertas de faturamento e custos para evitar surpresas e cobranças indevidas na conta da AWS durante a execução dos laboratórios práticos.

### [[03-024 Amazon S3]]
Apresenta o Amazon S3 como um dos blocos de construção fundamentais do armazenamento em nuvem, destacando sua escala quase infinita.

### [[03-025 Amazon S3 - Hands On]]
Laboratório prático mostrando como interagir com compartimentos (buckets) diretamente pelo console da AWS.

### [[03-026 Amazon S3 Security - Bucket Policy]]
Explica como criar políticas vinculadas ao IAM e Bucket Policies (segurança baseada em recursos) para conceder ou restringir o acesso apropriado.

### [[03-027 Amazon S3 Security - Bucket Policy - Hands On]]
Prática demonstrando os passos para permitir o acesso público a um objeto a partir das configurações do bucket e Bucket Policies.

### [[03-028 Amazon S3 - Versioning]]
Discute os fundamentos de como ativar o versionamento de arquivos e atualizar objetos de forma mais segura preservando seu histórico.

### [[03-029 Amazon S3 - Versioning - Hands On]]
Demonstra o processo e a visualização no ambiente AWS após o upload de arquivos de mesmo nome em um bucket com controle de versão habilitado.

### [[03-030 Amazon S3 - Replication]]
Orienta sobre as estratégias de Replicação Entre Regiões (CRR) ou Mesma Região (SRR) e seus casos de uso para backups e replicação assíncrona.

### [[03-031 Amazon S3 - Replication - Notes]]
Observações vitais sobre restrições na replicação de S3, enfatizando o uso de S3 Batch Replication se o usuário precisar replicar objetos gravados antes da regra existir.

### [[03-032 Amazon S3 - Replication - Hands On]]
Configuração prática em laboratório mostrando a união de um bucket de origem de onde os objetos fluem para outro de destino.

### [[03-033 Amazon S3 - Storage Classes]]
Define o detalhamento de custos vs. acessibilidade entre diferentes Storage Classes como Standard, IA, Intelligent Tiering, One-Zone e os modos Glacier.

### [[03-034 Amazon S3 - Storage Classes - Hands On]]
Prática focada em ajustar buckets e a classificação individual aplicada aos novos objetos transferidos para o S3.

### [[03-035 Amazon S3 Express One Zone]]
Discute e explica essa classe especificamente voltada a um altíssimo desempenho vinculada a uma única Zona de Disponibilidade e de latências rigorosas.

### [[03-036 Amazon S3 - Lifecycle Rules]]
Como aplicar Regras de Ciclo de Vida para deslocar os arquivos em um bucket de maneira escalonada ou expirar seus históricos por eficiência de custo.

### [[03-037 Amazon S3 - Lifecycle Rules - Hands On]]
O laboratório configurando regras transnacionais diretamente no console para migrar, transferir e transicional objetos com base na quantidade de dias na AWS.

### [[03-038 Amazon S3 - Event Notifications]]
Ensina sobre a arquitetura para gerenciar criações e exclusões através do rastreamento de notificações e como eles se comunicam interserviços.

### [[03-039 Amazon S3 - Event Notifications - Hands On]]
Elaboração prática demonstrando a verificação de gatilhos definidos garantindo os envios emitidos pelas movimentações do bucket do caso de uso.

### [[03-040 Amazon S3 - Performance]]
Estuda as considerações de escala e desempenho do Amazon S3 lidando com limites teóricos, First-Byte Latency e performance em massa (Throughput/RPS).

### [[03-041 Amazon S3 - Encryption]]
Trata dos principais métodos para criptografar o bucket por via Server-Side (SSE-S3 e SSE-KMS, entre outros) garantindo segurança do objeto.

### [[03-043 Amazon S3 - Encryption - Hands On]]
Aplica os fundamentos ativando o encadeamento das chaves de criptografia e gerenciando permissões para dados residentes em repouso no laboratório.

### [[03-044 Amazon S3 - Default Encryption]]
Esclarece a automação mandatório de SSE-S3 implantada como proteção por padrão, o qual cobre todos os novos objetos de maneira imperceptível ao usuário.

### [[03-045 Amazon S3 - Access Points]]
Mostra estratégias eficientes de particionamento e rotas de segurança em escala onde dezenas de clientes dividem o repasse das chamadas API pelo uso de Access Points.

### [[03-046 Amazon S3 Tables- Introduction and the Apache Iceberg Table Format]]
O lançamento de peso abordando as Tabelas S3 atrelado à integração nativa com formato líder Apache Iceberg para viabilizar ecossistemas abertos de Data Lakehouses.

### [[03-048 Amazon S3 Tables- Replicas and Security]]
Aborda a conveniência de habilitar pontos de backup das Tabelas baseadas nas S3-Tables em cópias de fácil implementação focadas em alta disponibilidade Read-Only.

### [[03-050 Amazon S3 - Storage Lens]]
Detalha o mecanismo focado na leitura de métricas avançadas sobre armazenamento a fim de prover visibilidade intra-organizacional na AWS.

### [[03-051 Amazon EBS]]
Transição para Elastic Block Store (EBS), explicando suas propriedades persistentes dentro do EC2, sendo focado em volumes diretos e atrelados por disponibilidade.

### [[03-052 Amazon EBS - Hands On]]
Demonstração sobre os anexos padrão para os componentes de raiz da instância bem como de volumes adicionais mapeados à máquina por debaixo dos panos.

### [[03-053 Amazon EBS Elastic Volumes]]
Fundamentos sobre como os volumes adquirem redimensionamentos quentes ou escalabilidade sem os típicos sacrifícios de downtime ou interrupções prévias.

### [[03-054 Amazon EFS]]
Mostra com afinco como o Amazon EFS resolve os problemas de arquivo compartilhado utilizando uma mecânica similar a um NFS gerenciado para ser atacado por milhares de conexões EC2 simultâneas.

### [[03-055 Amazon EFS - Hands On]]
Prática completa elaborando um compartilhamento EFS pela rede associado fielmente a uma VPC a partir de sua implantação guiada.

### [[03-056 Amazon EFS vs. Amazon EBS]]
Aula dedicada contrastando `[[Amazon EBS]]` para conectividade local de AZ individual contra os usos amplos do `[[Amazon EFS]]` focados na dispersão de leitura conjunta.

### [[03-057 AWS Backup]]
Garantias de conformidade com a centralidade na visão da plataforma sobre gerenciamento automatizado que evita que múltiplos scripts sejam forjados pelo administrador.

### [[03-058 AWS Backup - Hands On]]
Passos em tela demonstrando como a estruturação do plano central via AWS Backup ocorre em relação as outras opções existentes nativas aos serviços.

## Conexões Importantes
- Extensão do tópico S3: o Amazon S3 é base formadora crucial de todo o Data Lake, sendo referenciado de volta nas seções de Analytics a seguir, incluindo Athena e Glue.
- O estudo de S3 Storage Classes interage diretamente com S3 Lifecycle Rules para melhor gerenciamento de custos de Data Lakes com informações menos freqüentes (Cold Data).
- O confronto entre infraestrutura: A comparabilidade discutida na aula `[[03-056 Amazon EFS vs. Amazon EBS]]` mostra as restrições arquiteturais para casos de uso pontuais sendo de extrema relevância no exame da AWS.

## Observações
- Caso sua interface da AWS difira dos vídeos do aluno devido a novas visões da ferramenta, verifique as notas mencionadas na primeira hora com a ressalva na aula `[[03-022 [Important] AWS Console UI Update]]`.
- Como recomendado durante as provas de conceito, institua na conta principal os ensinamentos da aula `[[03-023 Set up an AWS Billing Alarm]]` para não causar danos financeiros quando laboratórios forem esquecidos ligados.
- A segurança principal reside no fato de que dezenas de buckets por default têm seu acesso "Block Public Access", devendo as definições de segurança ensinadas em `[[03-026 Amazon S3 Security - Bucket Policy]]` serem adotadas de modo manual.
