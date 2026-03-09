# Seção 05 - Sumário

## Visão Geral da Seção
A Seção 05 apresenta os recursos da Amazon AWS focados exclusivamente em projetos robustos de migração e transferências. Ela destrincha as ferramentas necessárias para trazer aplicativos, infraestrutura inteira corporativa (Data Centers) e bancos de dados volumosos para os ecossistemas flexíveis em nuvem da AWS em arquiteturas adequadas a escala Big Data.

## Conceitos Principais
- **Mapeamento e Levantamento Prévio:** Uso essencial de ferramentas avaliativas (Application Discovery Service) pré-migração.
- **DMS (Database Migration Service):** O padrão gerenciado focado em levar Bancos de Dados com resiliência, transicionando entre os mesmos motores (homogêneos) ou de conversão inter-motores heterogêneos usando Ferramentas Relacionais de Conversão (SCT).
- **DataSync vs Transfer Family:** A adoção de ferramentas da camada nativa otimizadas para mover petabytes de redes remotas usando agentes Data Sync; contrastando com ferramentas nativas tradicionais como FTP/SFTP suportadas ativamente perante serviços pelo Transfer Family mantendo compatibilidade com Active Directories da corporação.
- **Limitações Físicas da Rede e Borda Otimizada (AWS Snow Family):** A resposta criativa aos engarrafamentos extremos, falhas em larga escala ou indisponibilidade de links conectivos por meio da mobilização bruta on-premise nas "maletas" robustas da camada Snowball.
- **Fontes Alternativas Adotadas (Data Exchange):** Extensas contratações e integrações comerciais para assimilação garantida de pacotes formatados de grandes empresas direto no S3/Redshift da corporação com controle API de ponta-a-ponta.

## Resumo das Aulas

### [[05-106 Intro- Migration and Transfer]]
Garante a introdução e visão sobre os blocos temáticos e fundamentações desta breve seção tratando das metodologias e soluções focadas pontualmente em migração corporativa ágil em Data Engineer.

### [[05-107 Application Discovery Service & Application Migration Service]]
Contextualiza o passo primordial mapeando dependências, redes ocultas e performances operacionais nos bastidores com agentes corporativos locais, definindo uma eventual passagem controlada re-hospedável com os serviços MGN.

### [[05-108 AWS Database Migration Service (AWS DMS)]]
Fornece grande profundidade analítica demonstrando como orquestrar instâncias autorreplicáveis entre servidores com a fundação resiliente nativa de Failover da infraestrura DMS baseada em CDC (Change Data Capture) bem como a Schema Conversion Tool (SCT).

### [[05-109 AWS Database Migration Service (AWS DMS) - Hands On]]
Simula visualmente no ambiente operacional das AWS os endpoints conectivos que formam a ponte estrutural exigidas entre a "Origem" (Source) e o "Destino" (Target) em tarefas sem-servidor focadas e elásticas ao laboratório de migração.

### [[05-110 AWS DataSync]]
Um modelo gerenciado automatizável dotado unicamente por preservar o histórico POSIX (metadados nativos, autorizações SMB/NFS intocadas) agendando pontes pesadas (até 10 Gb/s) do On-Premise ao S3 ou EFS na malha da Amazon.

### [[05-111 AWS Snow Family]]
Detalha a substituição perante os colossais anos matemáticos em redes debilitadas (limitando e engarrafando os clusters) sendo suprimida fisicamente usando frentes portáteis modulares dotadas ou focadas de Armazenamento de Borda até Computações Otimizadas isoladas (Snowball).

### [[05-112 AWS Snow Family - Hands On]]
Incursões na interface de orçamentação elaborando a construção fictícia simuladora dos custos práticos, chaves operacionais encriptadas e processos unificados por trás de uma "importação" para o Amazon S3 utilizando maletas enviáveis das AWS.

### [[05-113 AWS Data Exchange]]
O mercado facilitado inter-empresarial assinado (subscrição na nuvem), capaz destribuir conjuntos de alto nível extraídos das imensas bases mercantis com repasse pronto aos pipelines como Machine Learning ou Redshift de forma rastreada via API da estrutura central. 

### [[05-114 AWS Transfer Family]]
Esclarece a ponte transparente amparando empresas no qual seu padrão estático logístico baseia-se num upload retro-compativel à interfaces rígidas (FTP, SFTP, FTPS), utilizando back-ends invisíveis como EFS ou S3 mascarados corporativamente sob DNS personalizados (Route 53).

## Conexões Importantes
- Muitas destrezas das transferências (FTP da família AWS Transfer ou o DataSync massivo POSIX) atuam servindo como elos vitais de extrações em rotas aos ecossistemas persistentes citados extensamente na Seção 03 como [[Amazon S3]] e [[Amazon EFS]].
- A Schema Conversion Tool (SCT) atrelada ao DMS vista na aula `[[05-108 AWS Database Migration Service (AWS DMS)]]` conecta o aprendizado de arquitetura entre grandes motores transnacionais em transições às esferas mais amplas apresentadas anteriomente na Aula de [[Amazon Redshift Intro & Architecture]].

## Observações
- A ferramenta mais essencial em exames referenciada à retenção dos metadados rigorosos num modelo de migração aos buckets ou Network File Systems da Amazon sempre esbarra na correta implementação demonstradas em práticas com [[AWS DataSync]], memorize esta exclusividade de POSIX retention!
- Casos complexos de Big Data englobam barreiras on-premises de latência de Rede. Conheça e avalie a regra de ouro das simulações da prova demonstradas em aula `[[05-111 AWS Snow Family]]` perante estimativas longas e inseguras focando na utilização bruta física off-line à sua viabilidade real Cloud.
