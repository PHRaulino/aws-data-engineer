---
description: Workflow de Geração de Quiz por Aula
---


Quando o usuário solicitar geração de perguntas para uma aula:

1. Identificar a aula.
2. Ler o `sumario/` da seção correspondente.
3. Ler a transcrição da aula em `Transcrições/`.
4. Gerar um arquivo CSV com perguntas baseado no conteúdo.
5. A liguagem das perguntas deve ser em Português.

---

# Local do arquivo gerado

O CSV deve ser salvo em: quizzes_csv/XX-XXX Nome da Aula.csv


Cada linha do CSV representa **uma pergunta**.

---

# Estrutura obrigatória do CSV

O arquivo deve seguir exatamente o seguinte formato: question,ref,answer,option_a,option_b,option_c,option_d


---

# Significado das colunas

| coluna | descrição |
|------|------------|
| question | pergunta |
| ref | aula utilizada como referência |
| answer | alternativa correta (A,B,C ou D) |
| option_a | alternativa A |
| option_b | alternativa B |
| option_c | alternativa C |
| option_d | alternativa D |

---

# Regras para perguntas verdadeiro ou falso

Para perguntas **True / False**:
answer = A (verdadeiro)
answer = B (falso)

Formato obrigatório:

option_a = Verdadeiro
option_b = Falso
option_c =
option_d =


---

# Regras obrigatórias de geração de perguntas

Para **cada aula**:

- gerar no mínimo **10 perguntas**
- idealmente entre **10 e 20 perguntas**

Tipos de perguntas permitidos:

- múltipla escolha
- verdadeiro ou falso
- cenários de arquitetura
- troubleshooting
- escolha de serviços AWS

---

# Foco obrigatório — Certificação AWS Data Engineer

Todas as perguntas devem ser elaboradas com mentalidade de **certificação AWS Data Engineer**.

Priorizar perguntas que envolvam:

- ingestão de dados
- processamento de dados
- armazenamento de dados
- catálogo de dados
- governança
- segurança e IAM
- monitoramento e observabilidade
- otimização de custo
- troubleshooting de pipelines

Sempre que possível, usar **perguntas situacionais (cenários)**.

Exemplo:

> Uma empresa precisa ingerir dados em tempo real com baixa latência e processar em Spark. Qual serviço AWS é mais apropriado?

---

# Caso a aula seja introdutória

Se o conteúdo da aula for:

- introdução
- overview de conceitos
- explicação superficial

Mesmo assim gerar **mínimo 10 perguntas**, focando em:

- entendimento arquitetural
- comparações entre serviços
- aplicação prática dos conceitos
- cenários derivados dos conceitos apresentados

---

# Regras de qualidade das perguntas

As perguntas devem:

- ser claras e objetivas
- ter apenas **uma resposta correta**
- evitar ambiguidades
- refletir cenários reais de engenharia de dados
- ajudar na preparação para exames AWS

---

# Exemplo de CSV gerado

question,ref,answer,option_a,option_b,option_c,option_d
Which AWS service is best suited for serverless ETL processing?,AWS Glue Introduction,A,AWS Glue,Amazon EMR,AWS Lambda,Amazon Athena
A company needs to query data directly from S3 using SQL without managing infrastructure. Which service should be used?,AWS Glue Introduction,C,Amazon Redshift,AWS Glue,Amazon Athena,Amazon EMR
AWS Glue Data Catalog can be used as a centralized metadata repository for analytics services.,AWS Glue Introduction,A,Verdadeiro,Falso,,
Which service is best suited for large-scale distributed Spark workloads with full cluster control?,AWS Glue Introduction,B,AWS Glue,Amazon EMR,Amazon Athena,AWS Lambda


---

# Checklist rápido de validação

Antes de concluir qualquer tarefa:

- [ ] Nenhum arquivo em `Transcrições/` foi alterado
- [ ] O sumário da seção (`sumario/`) foi consultado
- [ ] O CSV foi salvo no diretório correto (`quizzes_csv/`)
- [ ] Existem pelo menos **10 perguntas**
- [ ] Todas as perguntas seguem foco da certificação **AWS Data Engineer**