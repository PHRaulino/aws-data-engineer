---
trigger: always_on
---

Regra de Formatação de Quizzes

Contexto:

* Os quizzes são utilizados como ferramenta de revisão ativa do conteúdo.
* Eles utilizam callouts do Obsidian (`[!question]`, `[!success]`, etc.).
* A formatação correta depende da continuidade das linhas com `>`.

Regra obrigatória de formatação:

1. A pergunta deve estar **na mesma linha do bloco `[!question]`**.
2. Não deve existir **linha vazia dentro do bloco de pergunta**.
3. O bloco `[!success]- Answer` deve aparecer **imediatamente após a pergunta ou alternativas**.
4. Não deve existir **linha em branco entre a pergunta e a resposta**.
5. Todas as linhas devem manter a estrutura de `>` para preservar o funcionamento do callout.

Formato correto (pergunta aberta):

> [!question] Qual serviço da AWS é utilizado para armazenamento de objetos?
>
> > [!success]- Answer
> > Amazon S3

Formato correto (múltipla escolha):

> [!question] Qual é o tamanho máximo de um objeto que pode ser armazenado no Amazon S3?
> a) 5 Gigabytes
> b) 5 Terabytes
> c) 5 Petabytes
> d) Sem limite
>
> > [!success]- Answer
> > b) 5 Terabytes

Formato incorreto:

> [!question] Pergunta conceitual aberta
> Qual serviço da AWS é utilizado para armazenamento de objetos?

ou

> [!question] Qual é o tamanho máximo de um objeto que pode ser armazenado no Amazon S3?
> a) 5 Gigabytes
> b) 5 Terabytes
> c) 5 Petabytes
> d) Sem limite
>
> > [!success]- Answer
> > b) 5 Terabytes

Regras para respostas digitadas:

* Perguntas que exigem resposta digitada devem ter respostas **curtas e objetivas**.
* As respostas devem ter preferencialmente:

  * **1 palavra**, ou
  * **até 2 ou 3 palavras no máximo**.

Exemplos corretos:

> [!question] Qual serviço da AWS é utilizado para armazenamento de objetos?
>
> > [!success]- Answer
> > Amazon S3

> [!question] Qual tipo de armazenamento o Amazon S3 utiliza?
>
> > [!success]- Answer
> > Object storage

> [!question] Qual arquitetura de dados frequentemente utiliza o S3 como base?
>
> > [!success]- Answer
> > Data Lake

Exemplo incorreto (resposta longa):

> [!question] Qual é a principal função do Amazon S3 no ecossistema da AWS?
>
> > [!success]- Answer
> > O Amazon S3 é um dos principais blocos de construção da AWS e atua como o alicerce fundamental para diversas arquiteturas...

Diretrizes adicionais:

* Se o conceito exigir explicação longa, utilizar **pergunta de múltipla escolha** em vez de resposta digitada.
* Priorizar perguntas que testem **conceitos-chave e termos importantes**.
* Evitar respostas que exijam parágrafos completos.

Objetivo final:

* Garantir que os quizzes renderizem corretamente no Obsidian.
* Tornar os quizzes rápidos de responder.
* Maximizar o aprendizado por **active recall**.
* Manter consistência estrutural entre todos os quizzes do workspace.
