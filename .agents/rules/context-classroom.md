---
trigger: always_on
---

Regra de Contexto das Transcrições do Curso

Ordem de consulta de contexto:

1. Sumário da seção
2. Aula solicitada
3. Aulas relacionadas mencionadas no sumário
4. Outras aulas da seção, se necessário

Estrutura do projeto:

* A raiz do projeto contém as pastas `transcrições/` e `sumario/`.
* A pasta `transcrições/` contém as transcrições originais das aulas organizadas por seção.
* Dentro de `transcrições/`, os conteúdos estão organizados em diretórios como `Seção 01`, `Seção 02`, etc.
* Dentro de cada seção, existem arquivos de aulas com padrão como `01-001 Nome da Aula`, `02-033 Nome da Aula`, etc.
* A pasta `sumario/` contém os arquivos de sumário consolidados das seções.
* Cada seção possui um arquivo de sumário correspondente dentro de `sumario/`, que resume todas as aulas da seção e referencia as transcrições.

Exemplo de estrutura:

transcrições/

* Seção 01/

  * 01-001 Nome da Aula.md
  * 01-002 Nome da Aula.md
* Seção 02/

  * 02-001 Nome da Aula.md

sumario/

* Seção 01 - Sumário.md
* Seção 02 - Sumário.md

Regra obrigatória:

* Toda solicitação relacionada a uma aula específica deve considerar obrigatoriamente o arquivo de sumário da seção correspondente localizado em `sumario/` antes de analisar a transcrição completa da aula.
* O arquivo de sumário da seção deve ser tratado como fonte primária de contexto, visão geral, continuidade e relacionamento entre as aulas.
* A transcrição individual da aula deve ser usada como fonte complementar para aprofundamento, detalhes, exemplos, trechos específicos e extração de conteúdo mais granular.

Comportamento esperado:

1. Identificar a seção da aula solicitada.
2. Localizar o arquivo de sumário correspondente dentro da pasta `sumario/`.
3. Ler primeiro o sumário consolidado da seção.
4. Usar o sumário para entender:

   * o contexto geral da seção,
   * como a aula se conecta com as demais,
   * os principais temas já consolidados,
   * as referências entre aulas.
5. Consultar a transcrição específica da aula dentro de `transcrições/` para detalhar, expandir ou confirmar informações.
6. Caso seja necessário para melhor compreensão do tema, também consultar as transcrições de aulas relacionadas dentro da mesma seção ou mencionadas no sumário.
7. Utilizar essas aulas relacionadas para complementar contexto, esclarecer conceitos ou entender dependências entre conteúdos.
8. Sempre que possível, relacionar a resposta ao contexto da seção e não apenas ao conteúdo isolado da aula.

Diretrizes adicionais:

* Se houver divergência entre a interpretação isolada da aula e o contexto do sumário da seção, sinalizar a diferença explicitamente.
* Ao gerar resumos, mapas mentais, flashcards, explicações, questões ou materiais derivados de uma aula, manter alinhamento com o sumário consolidado da seção.
* Ao citar uma aula, preservar sua referência original no padrão de nomenclatura do projeto.
* Priorizar sempre a consistência entre o sumário da seção e o conteúdo das aulas individuais.
* Sempre que possível, utilizar o padrão de links do Obsidian (`[[...]]`) ao referenciar aulas ou conteúdos.
