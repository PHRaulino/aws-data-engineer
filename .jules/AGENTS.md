# Instruções do Jules para este workspace

Estas instruções adaptam as regras e workflows de `.agents/` para execução no Jules.

## Missão
Gerar materiais de estudo no vault Obsidian sem alterar as transcrições originais e mantendo forte conectividade entre notas.

## Políticas inegociáveis
1. **Somente leitura em `Transcrições/`**
   - Não editar, criar, renomear, mover ou excluir arquivos nessa pasta.
2. **Contexto primeiro no `sumario/`**
   - Antes de trabalhar uma aula, ler o sumário da seção correspondente.
3. **Referências com padrão Obsidian**
   - Usar sempre `[[Nome do Arquivo]]` para referências internas.
4. **Notas conectadas**
   - Evitar conteúdo isolado; criar conexões entre aulas, conceitos e seções.

## Playbook 1 — Sumário de seção
Entrada: pedido para criar/atualizar sumário de uma seção.

Passos:
1. Identificar seção e arquivo alvo `sumario/Seção XX - Sumário.md`.
2. Ler aulas da seção em `Transcrições/` (sem modificar).
3. Consolidar conceitos e progressão didática.
4. Criar/atualizar o sumário com links `[[...]]` para as aulas.

Estrutura sugerida:
- Visão Geral da Seção
- Conceitos Principais
- Resumo das Aulas
- Conexões Importantes
- Observações

## Playbook 2 — Quiz por aula
Entrada: pedido para criar/atualizar quiz de aula.

Passos:
1. Identificar aula e seção.
2. Ler `sumario/` da seção.
3. Ler transcrição da aula em `Transcrições/`.
4. Criar/atualizar `quizzes/XX-XXX Nome da Aula - Quiz.md`.

Frontmatter obrigatório:
```md
---
sources:
  - "[[Nome da Aula]]"
---
```

Regras do quiz:
- 6 a 10 perguntas.
- Cobrir entendimento conceitual.
- Incluir múltipla escolha, V/F, associação e múltiplas respostas.
- Em perguntas abertas, resposta curta e objetiva.

Diretriz extra de preparação para certificação:
- Todo quiz deve ser gerado com foco em preparação para a certificação **AWS Data Engineer**.
- Priorizar questões de cenário e resolução de problemas, exigindo escolha e uso de serviços AWS para fixar o conteúdo da aula.
- Cobrar decisões de arquitetura e operação (serviço correto, trade-offs, segurança, governança, desempenho e custo).

Formatação obrigatória dos callouts:
- `> [!question]` com enunciado na mesma linha.
- Sem quebra indevida no bloco.
- Resposta logo abaixo com `> > [!success]- Answer`.

## Qualidade e segurança
- Confirmar que nenhuma alteração ocorreu em `Transcrições/`.
- Garantir consistência com a seção e links entre notas.
- Salvar materiais derivados em pastas apropriadas (`sumario/`, `quizzes/`, `Flashcards/`).
