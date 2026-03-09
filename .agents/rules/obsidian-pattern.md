---
trigger: always_on
---

Regra de Referência entre Arquivos (Padrão Obsidian)

Contexto:

* O workspace utiliza o Obsidian para organização e navegação do conhecimento.
* Portanto, todas as referências entre arquivos devem seguir o padrão de link interno do Obsidian.

Regra obrigatória:

* Sempre que for necessário referenciar outro arquivo do projeto, deve ser utilizado o padrão de link interno do Obsidian utilizando colchetes duplos: [[Nome do Arquivo]].

Diretrizes de uso:

* O nome dentro do link deve corresponder exatamente ao nome do arquivo referenciado.
* Não utilizar caminhos relativos ou absolutos quando não forem necessários.
* Priorizar sempre o link simples utilizando apenas o nome do arquivo.

Exemplo:
[[01-003 Introdução ao Data Lake]]

Referenciando uma aula dentro de texto:
"A explicação sobre partições foi introduzida anteriormente em [[02-014 Particionamento em Data Lakes]]."

Boas práticas:

* Sempre que um conceito depender diretamente de outra aula, criar o link entre elas utilizando [[...]].
* Se o sumário de uma seção mencionar uma aula específica, ele deve usar o link interno do Obsidian para facilitar a navegação.
* Evitar referências em texto puro quando um link navegável puder ser criado.

Diretriz sobre títulos dos arquivos:

* O nome do arquivo já representa o título da nota dentro do Obsidian.
* Portanto, não deve ser utilizado um título H1 (`#`) no início do arquivo.
* O conteúdo da nota deve começar diretamente com texto, ou no máximo com subtítulos (`##`, `###`) quando necessário para estruturar o conteúdo.
* Isso evita redundância entre o nome do arquivo e o conteúdo da nota.

Exemplo correto:

Conteúdo inicial do arquivo:
Introdução ao conceito de Data Lakes e sua relação com arquiteturas modernas de dados.

## Conceitos principais

* Armazenamento escalável
* Schema on read
* Separação entre armazenamento e processamento

Exemplo incorreto:

# Introdução ao Data Lake

Diretriz adicional:

* Sempre que possível, utilizar os links para fortalecer a conexão entre aulas, conceitos e seções, permitindo navegação bidirecional dentro do vault.
