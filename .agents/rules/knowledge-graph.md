---
trigger: always_on
---

Regra de Navegação e Conexão de Conhecimento

Contexto:

* O workspace utiliza o Obsidian como sistema de organização de conhecimento.
* O objetivo do workspace não é apenas armazenar informações, mas construir um grafo de conhecimento navegável entre aulas, conceitos e seções.

Princípio fundamental:

* Nenhuma nota ou material gerado deve existir de forma isolada.
* Sempre que possível, o conteúdo deve ser conectado a outras aulas, conceitos ou seções do curso.

Regra obrigatória:

* Ao gerar qualquer conteúdo (resumos, notas, explicações, mapas mentais, insights ou materiais de estudo), o agente deve identificar possíveis conexões com outros conteúdos do workspace e criar links utilizando o padrão do Obsidian `[[...]]`.

Tipos de conexões que devem ser criadas:

1. Conexões entre aulas

* Quando uma aula mencionar ou depender de um conceito apresentado em outra aula, criar um link entre elas.

Exemplo:
"O conceito de particionamento já foi introduzido anteriormente em [[02-014 Particionamento em Data Lakes]]."

2. Conexões com o sumário da seção

* Sempre que uma aula ou conceito fizer parte de uma seção, referenciar o sumário correspondente.

Exemplo:
"Este tema faz parte da progressão apresentada no [[Seção 03 - Sumário]]."

3. Conexões entre conceitos

* Quando um conceito estiver relacionado a outro conceito já explicado em outra parte do workspace, criar um link entre eles.

Exemplo:
"O Glue utiliza metadados armazenados no [[AWS Glue Data Catalog]]."

4. Conexões de continuidade de aprendizado

* Se uma aula prepara o terreno para outra aula futura, essa relação deve ser explicitada.

Exemplo:
"Este conceito será aprofundado posteriormente em [[04-007 Otimização de Queries no Athena]]."

Boas práticas:

* Priorizar sempre o uso de links internos em vez de referências em texto simples.
* Sempre utilizar o padrão `[[Nome do Arquivo]]`.
* Manter consistência no nome dos arquivos referenciados.
* Criar conexões naturais que ajudem na navegação e no entendimento do conteúdo.

Diretrizes adicionais:

* Evitar duplicação de explicações quando um conceito já estiver documentado em outra nota; preferir criar um link.
* Sempre que possível, conectar novos conteúdos ao sumário da seção correspondente.
* Priorizar a construção de um grafo de conhecimento rico e navegável dentro do vault.

Objetivo final:

* Transformar o vault em um sistema de conhecimento interconectado, onde seja possível navegar entre aulas, conceitos e seções de forma natural através dos links do Obsidian.
