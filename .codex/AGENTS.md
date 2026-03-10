# Instruções do Codex para este workspace

Estas instruções adaptam as regras e workflows de `.agents/` para o comportamento do Codex.

## Escopo e objetivo
- O vault é usado no Obsidian para estudo de AWS Data Engineering.
- O objetivo é produzir materiais derivados navegáveis (sumários, quizzes, notas, flashcards), conectados por links internos `[[...]]`.

## Regras obrigatórias

### 1) `Transcrições/` é somente leitura
- Nunca criar, editar, mover ou remover arquivos dentro de `Transcrições/`.
- As transcrições são fonte primária imutável.
- Se o usuário pedir alteração em `Transcrições/`, recusar e sugerir gerar material derivado em outro diretório.

### 2) Ordem de contexto para tarefas de aula
Sempre seguir esta ordem:
1. Ler o sumário da seção em `sumario/`.
2. Ler a aula solicitada em `Transcrições/`.
3. Ler aulas relacionadas citadas no sumário (se necessário).
4. Ler outras aulas da seção (se necessário).

### 3) Padrão de links Obsidian
- Toda referência entre arquivos deve usar `[[Nome do Arquivo]]`.
- Evitar caminhos longos quando o nome da nota já resolve a navegação.
- Em notas novas, não usar H1 (`#`) no início quando o nome do arquivo já é o título.

### 4) Construção de grafo de conhecimento
Ao gerar conteúdo:
- Criar links para aulas relacionadas.
- Ligar ao sumário da seção (`[[Seção XX - Sumário]]`).
- Ligar conceitos correlatos já existentes.
- Explicitar continuidade de aprendizado (pré-requisito e próximos passos).

## Workflow A — criar/atualizar sumário de seção
Quando pedirem sumário de seção:
1. Identificar a seção alvo.
2. Ler aulas da seção em `Transcrições/`.
3. Criar/atualizar arquivo em `sumario/Seção XX - Sumário.md`.
4. Preservar estrutura existente quando já houver arquivo.
5. Manter aulas na ordem original da seção.
6. Incluir links `[[...]]` para todas as aulas citadas.

Estrutura recomendada:
- Visão Geral da Seção
- Conceitos Principais
- Resumo das Aulas
- Conexões Importantes
- Observações

## Workflow B — criar/atualizar quiz de aula
Quando pedirem quiz:
1. Identificar a aula.
2. Ler `sumario/` da seção correspondente.
3. Ler a transcrição da aula em `Transcrições/`.
4. Criar/atualizar `quizzes/XX-XXX Nome da Aula - Quiz.md`.

Formato obrigatório do quiz:

```md
---
sources:
  - "[[Nome da Aula]]"
---
```

Regras de conteúdo:
- Entre 6 e 10 perguntas.
- Cobrir conceitos-chave, definições, comparações e práticas.
- Misturar tipos: múltipla escolha, verdadeiro/falso, associação, múltiplas respostas.

Regras de formatação (callouts):
- Pergunta na mesma linha de `> [!question] ...`.
- Sem linha em branco indevida dentro do bloco.
- Resposta imediatamente após pergunta/opções:
  - `> > [!success]- Answer`
- Respostas digitadas curtas (1 a 3 palavras, preferencialmente).

## Checklist rápido de validação
Antes de concluir qualquer tarefa:
- [ ] Nenhum arquivo em `Transcrições/` foi alterado.
- [ ] Há links `[[...]]` para navegação.
- [ ] O contexto da seção (`sumario/`) foi consultado.
- [ ] O artefato foi salvo no diretório correto (`sumario/`, `quizzes/`, etc.).
