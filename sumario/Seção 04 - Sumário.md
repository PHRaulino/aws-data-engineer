# Seção 04 - Sumário

## Visão Geral da Seção
A Seção 04 explora profundamente as ofertas de banco de dados da AWS. A seção cobre uma ampla variedade de tecnologias que vão desde bancos de dados NoSQL totalmente gerenciados (DynamoDB) e serviços de banco de dados relacionais (Amazon RDS, Amazon Aurora), até soluções para Big Data e Data Warehousing escaláveis como o Amazon Redshift. O curso detalha os diferentes modelos e casos de uso, focando em como esses serviços se integram para engenharia de big data, ajuste de desempenho e arquiteturas baseadas em nuvem.

## Conceitos Principais
- **Bancos de Dados NoSQL:** Amazon DynamoDB (com foco em conceitos de RCU/WCU, LSIs/GSIs, Streams, DAX, Time To Live, e conectividade com S3), DocumentDB (MongoDB), e Keyspaces (Cassandra).
- **Bancos de Dados Relacionais e Em Memória:** Amazon RDS, Amazon Aurora (inclusive atuando como Vector Store com o pgvector), e MemoryDB para Redis.
- **Bancos de Dados Gráficos e de Séries Temporais:** Amazon Neptune e Amazon Timestream.
- **Data Warehousing (Amazon Redshift):** Arquitetura distribuída, Redshift Spectrum, Distribuição de Dados, Durabilidade, comandos como COPY e Integrações com outros serviços.
- **Conceitos Avançados do Redshift:** Materialized Views, Serverless, Federated Queries, UDFs do Lambda, Redshift Data API, e Data Sharing.

## Resumo das Aulas

### [[04-059 Intro- Database]]
Introdução abrangente abordando o panorama das tecnologias de bancos de dados da Amazon (DynamoDB, RDS, Neptune, Redshift) que serão destrinchadas detalhadamente ao longo do módulo visando os exames de certificação.

### [[04-060 Amazon DynamoDB]]
Apresenta o DynamoDB como um banco de dados NoSQL sem servidor, detalhando seu contraste com RDBMS tradicionais e suas aplicações ideais dentro de arquiteturas cloud nativas.

### [[04-061 Amazon DynamoDB - Hands On]]
Prática focada na criação sem servidor da infraestrutura inicial de tabelas do DynamoDB e identificação chaves primárias e de ordenação através da interface da AWS.

### [[04-062 Amazon DynamoDB in Big Data]]
Casos de uso aplicáveis do DynamoDB para o mundo de Big Data (ingestão rápida log, interações web, jogos, etc), identificando onde o serviço se destaca e seus anti-padrões.

### [[04-063 Amazon DynamoDB - Throughput (RCU & WCU)]]
Expõe as mecânicas financeiras e de limites entre a configuração da capacidade pré-provisionada calculada pelas Unidades de Leitura (RCU) e Unidades de Gravação (WCU).

### [[04-064 Amazon DynamoDB - Throughput (RCU & WCU) - Hands On]]
Laboratório simulando a manipulação e troca sob demanda/provisionada das variáveis RCU/WCU na mesa de tabelas para escalar performance sob controle.

### [[04-065 Amazon DynamoDB - Basic APIs]]
Analisa como as APIs específicas (PutItem, UpdateItem, e outras) afetam registros individualmente durante interações programadas ao longo do banco de dados na nuvem.

### [[04-066 Amazon DynamoDB - Basic APIs - Hands On]]
O aluno utiliza da AWS Interface para visualizar manipulações usando Scan e a realização das APIs vitais em tempo real criando novos atributos dentro do DynamoDB.

### [[04-067 Amazon DynamoDB - Indexes (LSI & GSI)]]
Classifica a importância dos índices operando como atalhos para colunas complexas através de Índices Secundários Locais (criados e rígidos na fundação) e Globais.

### [[04-068 Amazon DynamoDB - Indexes (LSI & GSI) - Hands On]]
Vislumbre focado em construir uma Tabela em que Chaves de Classificações Paralelas e LSI/GSIs são geridas na prática para consulta ampliada.

### [[04-069 Amazon DynamoDB - PartiQL]]
Apresenta PartiQL como uma transição que unifica bancos sem-esquema com uma familiaridade trazida aos desenvolvedores usando SQL puro manipulando Dynamo.

### [[04-070 Amazon DynamoDB Accelerator (DAX)]]
Detalha como mitigar picos de acesso repentino de Leitura nos nós "Hot Keys", empregando uma camada em tempo real de contorno cache gerenciado pelo DAX.

### [[04-071 Amazon DynamoDB Accelerator (DAX) - Hands On]]
Demonstração das escolhas estruturais na criação real dos clusters tipo (R / T) DAX com ênfase no não provisionamento no Free Tier AWS. 

### [[04-072 Amazon DynamoDB - Streams]]
Ensina arquitetura reativa utilizando as capacidades ordenadas do DynamoDB Streams para interceptar modificações e direcioná-las a plataformas como AWS Kinesis ou Lambda.

### [[04-073 Amazon DynamoDB - Streams - Hands On]]
Aplicação habilitando visualizações dos Streams exportados demonstrando a ponte nativa serviless para os gatilhos em processamento de tempo real com AWS Lambda.

### [[04-074 Amazon DynamoDB - Time To Live (TTL)]]
O mecanismo que isenta os operadores do Dynamo de encargos na gravação durante expurgação natural dos dados expiratórios usando restrições de tempo UNIX.

### [[04-075 Amazon DynamoDB - Patterns with S3]]
Ilustra táticas híbridas armazenando os ponteiros e metadados no DynamoDB e descarregando os Blobs excessivamente densos em buckets para economizar recursos.

### [[04-076 Amazon DynamoDB - Security]]
Detalha VPC Endpoints e conexões privadas dentro de ecossistemas protegidos em paralelo a PITR Backup sem afetação na camada KMS.

### [[04-077 Amazon RDS]]
Passa em revisão os conceitos familiares dos mecanismos gerenciados RDBMS (PostgreSQL, MySQL e clones), servindo de referência pontual embora não projetado com exclusividade ao Big Data.

### [[04-078 Shared and exclusive locks in RDS]]
Um foco particular em Concorrência em RDS destacando a necessidade e os papéis dos Exclusive/Shared Locks garantindo as transações nas malhas relacionais.

### [[04-079 Amazon RDS Best Practices]]
Conselhos práticos na gerência diária operatória: Alinhamento e monitoramento ativo nas métricas Cloudwatch combinadas às programações vitais de backups fora do pico da instância. 

### [[04-080 Amazon Aurora]]
Discute a reescritura revolucionária proposta pala arquitetura da AWS contornando barreiras em Bancos Compátiveis, garantindo replicação sub-milissegundo para os mecanismos Postgres/MySQL.

### [[04-081 Amazon Aurora - Hands On]]
Etapas acompanhadas implantando as estruturas robustas Clusterizando do zero instâncias Aurora demonstrando seleções primárias e escalabilidade imediata do produto.

### [[04-082 Aurora as a Vector Store with pgvector]]
Apresentação pontual do Aurora capacitado como repositório otimizado vetorizado aos casos AI/ML RAG graças em paralelo ao robustecimento da extensão `pgvector`. 

### [[04-083 Amazon DocumentDB]]
Alternativa nativa à prova dimensional (Aurora Edition) suportada as consultas aos legados com conectividade para formato MongoDB sem servidor e orientada a Documentos.

### [[04-084 Amazon MemoryDB for Redis]]
Esclarece as sútis mas reais divergências atrelando um armazenamento Redis dotado do log em Multi-AZ sem comprometer a latência baseada num Memory Database ultra acelerado.

### [[04-085 Amazon Keyspaces (for Apache Cassandra)]]
Um produto elástico gerenciado que toma posse da responsabilidade sem servidor para o processamento unificado multi-region nas instâncias nativas Cassandra CQL do usuário.

### [[04-086 Amazon Neptune]]
A incursão sobre Bases Gráficas na nuvem com Amazon Neptune para gerir vértices que espelham relações infinitamente circulares nativas das Teias das Redes Sociais ou detecção aprimorada Fraude. 

### [[04-087 Amazon Neptune - Query Languages]]
Ressalta que exames requerem familiaridade nos protocolos compatíveis na AWS para Graph (Gremlin, Cypher e SPARQL).

### [[04-088 Amazon Timestream]]
Explicitações de propósitos vitais que cercam logs cronológicos ultra gerenciados dotados de vida cíclica automatizadas em bilhões de coletas temporais pelo Amazon Timestream.

### [[04-089 Amazon Redshift Intro & Architecture]]
Inicia mergulho prolongado na suíte do Amazon Redshift abordando Data Warehouses MPP clusterizados e perfeitamente calibrados voltados unicamente para a alta demanda do engenheiro de dados.

### [[04-090 Redshift Spectrum and Performance Tuning]]
Explora a flexibilidade expandida capaz de quebrar fronteiras locais processando de forma delegada com o Spectrum usando nós dedicados em dados dispersos em S3 (Lakehouse).

### [[04-091 Redshift Durability and Scaling]]
Mostra a resiliência tri-dimensional natural aos aglomerados em funcionamento providenciados pelo espelhamento S3 entre blocos computacionais atenuando desastres catastróficos acidentais.

### [[04-092 Redshift Distribution Styles]]
Profundamente testável, define com nitidez os esquemas (EVEN, ALL, KEY, e tolerância AUTO) que reescrevem o modo como as tabelas interagem fisicamente minimizando movimentações no processador.

### [[04-093 Redshift Data Flows and the COPY command]]
Ensina os caminhos preferenciais nas extrações pesadas de Redshift usando fluxos multi-threaded paralelizados orquestrados sobre a execução autêntica performática com a cláusula estrutural COPY. 

### [[04-094 Redshift Integration - WLM - Vacuum]]
O WLM é trazido à discussão junto às ligações entre variados serviços e comandos vitais, bem a essência da reciclagem em segundo plano via VACUUM nas engrenagens logísticas do Redshift.

### [[04-095 Redshift Resizing]]
Estuda táticas redimensionando elásticas do Redshift limitando latência na adição computacional frente a reinicialização massiva ou Classic Resizing com migrações de snapshot base zero.

### [[04-096 RA3 Nodes, Cross-Region Data Sharing, Redshift ML]]
Fundamentos cruciais nodesacoplamento das métricas com nós do formato Storage Otimizado AWS RA3 bem as extensões aos Data-share e a adoção contínua nos cálculos analíticos com Machine Learning nativo.

### [[04-097 Redshift Security]]
Um resumo pontual evidenciando práticas a nível granular ressaltando migrações críticas envolvendo Módulos Dedicados Hardwares tipo as complexas replicações e aprovações HSM Clusters.

### [[04-098 Redshift Serverless]]
Apresenta o movimento AWS aos data-warehousing focados numa abstração isenta pre-configurada e totalmente elástica que provisiona Data Analytics transitoriamente baseados atrelados sob o uso da cobrança unificada RCUs.

### [[04-099 Redshift Materialized Views]]
Acentua otimizações de Visualizações Materializadas, guardando relatórios completos processados anteriormente visando diminuir oneração e tempo entre cruzamentos pesados analíticos sob uso de snapshots.

### [[04-100 Redshift Data Sharing - Data Shares]]
Mecanismo isolando provedores de sub-clusters dedicados evitando congestionamentos paralelos na transferência assíncrona baseada por aprovação sobre nós que buscam acesso sem recálculo principal. 

### [[04-101 Redshift Lambda UDF]]
Como funções heterogêneas sob os gatilhos lambdas flexíveis conectam requisições impensáveis às estruturas AWS integrando com Redshift permitindo chamadas contíguas à web ou tradução dinâmica local.

### [[04-102 Redshift Federated Queries]]
Cobre interconexões lógicas consultando bancos operacionais em estado fluido vivo no PostgresRDS reduzindo latência no uso ETL centralizando Data Warehouse no Amazon Redshift.

### [[04-103 Redshift System Tables and System Views]]
Elucida as consultas do núcleo, esmiuçando logs analgésicos sob SYS e SVV demonstrando visão na raiz de processos bloqueantes ou lentos durante exploração forense analítica local.

### [[04-104 Redshift Data API]]
O laboratório teórico cobrindo REST gateways que fornecem rotas API para arquiteturas desvinculadas contornadas pelo tráfego corporativo conectando com a estrutura transnacional no modelo Event-Driven SDK Redshift.

## Conexões Importantes
- Muitas das funcionalidades do **DynamoDB** fazem integrações com soluções de outras secções (Armazenamento [[Amazon S3]] para contornar limitação de 400KB e eventos no Kinesis).
- A seção se conecta intensamente com o Data Warehousing moderno destacando o **Redshift Spectrum**, similar ao funcionamento e complementar da query de data lakes visto posteriormente com **Amazon Athena**.
- As táticas com **Vector Store** baseadas no pgvector com [[Amazon Aurora]] conectam a estrutura básica transicional aos recursos RAG e de conhecimento para Machine Learning.

## Observações
- O DynamoDB RCU/WCU e o mecanismo de dimensionamento podem aparecer repetidamente no exame e devem ser dominados com atenção especial se você busca aprovação na certificação AWS.
- Compreenda perfeitamente a diferença entre os Estilos de Distribuição (`KEY`, `EVEN`, `ALL` e `AUTO`) no Redshift apontados na aula [[04-092 Redshift Distribution Styles]], eles compõem um ponto-chave de arquitetura da plataforma e do curso.
