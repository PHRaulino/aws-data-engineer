---
trigger: always_on
---

Regra de Proteção das Transcrições

Contexto:

* O diretório `transcrições/` contém as transcrições originais das aulas do curso.
* Esses arquivos são considerados a fonte primária e imutável do conteúdo do curso.

Regra obrigatória:

* Nenhum agente, automação ou processo pode criar, modificar, reescrever, resumir, complementar ou remover conteúdo dentro da pasta `transcrições/`.
* O conteúdo dessa pasta deve ser tratado como **somente leitura (read-only)**.

Restrições explícitas:
É estritamente proibido:

* Alterar qualquer arquivo dentro de `transcrições/`.
* Criar novos arquivos dentro de `transcrições/`.
* Atualizar, corrigir ou melhorar textos das transcrições.
* Inserir links, comentários, metadados ou qualquer outro tipo de anotação dentro das transcrições.

Comportamento esperado:

* As transcrições podem ser **lidas e utilizadas como referência**, mas nunca modificadas.
* Qualquer conteúdo derivado (resumos, notas, mapas mentais, explicações, flashcards, etc.) deve ser gerado **fora do diretório `transcrições/`**.
* Caso seja necessário criar materiais derivados, eles devem ser colocados em outros diretórios apropriados do workspace.

Tratamento de solicitações do usuário:

* Se o usuário solicitar qualquer alteração dentro da pasta `transcrições/`, o agente deve **recusar a ação**.
* A resposta deve informar claramente que essa operação é proibida por uma regra explícita do workspace.

Exemplo de resposta esperada:

"Não posso realizar essa alteração.
As regras do workspace proíbem explicitamente criar ou modificar qualquer arquivo dentro do diretório `transcrições/`, pois ele contém as transcrições originais das aulas e é tratado como conteúdo somente leitura."

Diretriz adicional:

* Sempre preservar a integridade das transcrições originais.
* Nunca sugerir alterações indiretas que resultem em modificação dentro da pasta `transcrições/`.
