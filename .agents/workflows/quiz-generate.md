---
description: Workflow de Geração de Quiz por Aula
---

Contexto:

* O workspace possui transcrições de aulas dentro da pasta `transcrições/`.
* Existe uma pasta `quizzes/` na raiz do projeto destinada à criação de quizzes baseados nas aulas.
* Os quizzes devem ser utilizados como ferramenta de estudo e revisão do conteúdo.

Estrutura esperada:

transcrições/

* Seção XX/

  * XX-XXX Nome da Aula.md

quizzes/

* XX-XXX Nome da Aula - Quiz.md

Objetivo:

* Gerar um quiz completo baseado no conteúdo de uma aula específica para reforçar o aprendizado e revisar os principais conceitos apresentados pelo instrutor.

Regra obrigatória:

* Sempre que o usuário solicitar a criação de um quiz para uma aula, o arquivo deve ser criado dentro da pasta `quizzes/`.
* O agente nunca deve modificar os arquivos dentro de `transcrições/`.

Comportamento esperado:

1. Identificar a aula indicada pelo usuário.
2. Localizar a transcrição da aula dentro de `transcrições/`.
3. Consultar também o sumário da seção correspondente em `sumario/` para entender o contexto geral da aula.
4. Ler a transcrição da aula e identificar:

   * conceitos principais
   * definições importantes
   * práticas recomendadas
   * comparações ou diferenças entre tecnologias
   * exemplos explicados pelo instrutor
5. Gerar um quiz completo cobrindo os pontos principais da aula.
6. Criar ou atualizar o arquivo de quiz correspondente dentro da pasta `quizzes/`.

Formato do arquivo:

O quiz deve seguir exatamente esta estrutura:

---

sources:

* "[[Nome da Aula]]"

---

Tipos de perguntas permitidos:

* múltipla escolha
* verdadeiro ou falso
* associação de conceitos
* perguntas de múltiplas respostas

Exemplo de estrutura:

> [!question] Pergunta de múltipla escolha
> a) opção A
> b) opção B
> c) opção C
> d) opção D
>
> > [!success]- Answer
> > resposta correta

> [!question] Pergunta de múltiplas respostas
> a) opção A
> b) opção B
> c) opção C
> d) opção D
>
> > [!success]- Answer
> > a) opção A
> > c) opção C

> [!question] Associação de conceitos
>
> > [!example] Group A
> > a) termo
> > b) termo
>
> > [!example] Group B
> > x) definição
> > y) definição
>
> > [!success]- Answer
> > a) -> x)
> > b) -> y)

> [!question] Verdadeiro ou falso
>
> > [!success]- Answer
> > True

Diretrizes de geração do quiz:

* O quiz deve conter entre **6 e 10 perguntas**.
* As perguntas devem cobrir os conceitos mais importantes da aula.
* Sempre incluir diferentes tipos de perguntas permitidos.
* As respostas devem ser claras e objetivas.
* As perguntas devem priorizar entendimento conceitual.

Referências obrigatórias:

* O campo `sources` deve conter um link para a aula utilizando o padrão do Obsidian.

Exemplo:

---

sources:

* "[[10-209 Key Salting]]"

---

Diretrizes adicionais:

* Sempre utilizar o padrão de links do Obsidian `[[...]]`.
* O quiz deve servir como ferramenta de revisão do conteúdo da aula.
* As perguntas devem focar em entendimento conceitual e não apenas memorização literal.
* O conteúdo deve refletir fielmente o que foi explicado na aula.

Resultado esperado:

* Um arquivo de quiz completo dentro da pasta `quizzes/` que permita revisar rapidamente os conceitos mais importantes da aula dentro do Obsidian.
