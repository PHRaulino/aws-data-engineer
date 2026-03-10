---
description: gerar roteiro de podcast da aula
---

Quando o usuário solicitar um **roteiro de podcast para uma aula**, o agente deve gerar um **arquivo JSON estruturado** contendo um roteiro de conversa entre personagens baseado no conteúdo da aula.

Esse roteiro será utilizado para gerar áudio via **ElevenLabs TTS**.

---

# Ordem obrigatória de leitura

Seguir a mesma ordem de contexto:

1. Ler o sumário da seção em `sumario/`.
2. Ler a aula solicitada em `Transcrições/`.
3. Ler aulas relacionadas citadas no sumário (se necessário).
4. Ler outras aulas da seção (se necessário).

⚠️ Nunca alterar arquivos dentro de `Transcrições/`.

---

# Local do arquivo gerado

O roteiro deve ser salvo em:

```
podcasts/
XX-XXX Nome da Aula.json
```

Cada item do array representa **uma fala de um personagem**.

---

# Estrutura obrigatória do JSON

O arquivo deve conter **um array de objetos** com a seguinte estrutura:

```json
[
  {
    "character": "Nome do personagem",
    "text": "Texto da fala com instruções de entonação e estilo"
  }
]
```

Campos obrigatórios:

| campo     | descrição                                 |
| --------- | ----------------------------------------- |
| character | personagem que fala                       |
| text      | texto da fala que será enviado para o TTS |

---

# Personagens recomendados

O roteiro deve usar **2 a 3 personagens** para manter a conversa dinâmica.

Exemplo:

* **Host** → conduz o episódio
* **Especialista** → explica conceitos técnicos
* **Curioso** (opcional) → faz perguntas que ajudam a reforçar o aprendizado

---

# Estilo do podcast

O roteiro deve ser:

* didático
* conversacional
* natural
* envolvente

Evitar leitura mecânica.

O objetivo é transformar a aula em um **episódio curto de podcast educativo**.

---

# Duração recomendada

O roteiro deve gerar **entre 5 e 10 minutos de áudio**.

Isso normalmente equivale a aproximadamente:

* **800 a 1200 palavras**

Distribuídas entre os personagens.

---

# Instruções para ElevenLabs (entonação)

Como o texto será utilizado em **ElevenLabs**, o agente deve enriquecer as falas com sugestões de entonação natural, por exemplo:

* pausas curtas
* mudança de tom
* ênfase em termos importantes
* estilo conversacional

Exemplo dentro do texto:

```
"Hoje vamos falar sobre AWS Glue... *pausa curta* ...um dos serviços mais importantes para ETL serverless na AWS."
```

ou

```
"Agora presta atenção nisso: o Glue usa Spark por baixo dos panos — e isso muda completamente como você escala pipelines."
```

---

# Regras de qualidade

O roteiro deve:

* explicar conceitos importantes da aula
* conectar com aplicações reais de engenharia de dados
* usar exemplos práticos
* reforçar entendimento para certificação AWS Data Engineer

---

# Estrutura recomendada do episódio

O roteiro deve seguir aproximadamente este fluxo:

1. **Introdução do episódio**
2. **Contexto do problema**
3. **Explicação do conceito principal**
4. **Exemplo prático**
5. **Resumo do aprendizado**
6. **Conexão com próximos tópicos**

---

# Exemplo de JSON gerado

```json
[
  {
    "character": "Host",
    "text": "Bem-vindo ao Data Engineering Cast! Hoje vamos falar sobre AWS Glue... *pausa curta* ...um serviço fundamental quando pensamos em pipelines de dados serverless na AWS."
  },
  {
    "character": "Curioso",
    "text": "Mas espera aí... quando você diz serverless ETL, isso significa que eu não preciso gerenciar cluster nenhum?"
  },
  {
    "character": "Especialista",
    "text": "Exatamente. O AWS Glue gerencia toda a infraestrutura por você. Por baixo dos panos ele utiliza Apache Spark... *ênfase leve* ...o que permite processar grandes volumes de dados distribuídos."
  },
  {
    "character": "Host",
    "text": "Então imagina o seguinte cenário: você tem dados chegando no S3 todos os dias e precisa transformar esses dados para análise no Athena ou Redshift."
  },
  {
    "character": "Especialista",
    "text": "Nesse caso você pode usar um job do Glue para ler os arquivos no S3, transformar os dados e gravar novamente no data lake já no formato otimizado."
  }
]
```

---

# Checklist obrigatório

Antes de concluir:

* [ ] Nenhum arquivo em `Transcrições/` foi alterado
* [ ] O sumário da seção foi consultado
* [ ] O JSON foi salvo em `podcasts/`
* [ ] O roteiro possui múltiplos personagens
* [ ] O conteúdo é conversacional e didático
* [ ] O episódio reforça conceitos relevantes para AWS Data Engineer

---

💡 **Sugestão forte para seu caso**

Se quiser, posso também montar um **Workflow D muito poderoso**, que gera automaticamente:

* **podcast + quiz + resumo técnico**
* tudo **a partir de uma aula**

Ou seja:

```
Transcrição → resumo → quiz → podcast → flashcards
```

Isso transforma seu vault praticamente em um **sistema automático de aprendizado ativo** para certificação AWS.
