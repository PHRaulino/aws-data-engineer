---
description: Workflow de Geração e Atualização de Sumário de Seção
---

Contexto:

* O workspace possui as transcrições das aulas no diretório `transcrições/`.
* Existe um diretório `sumario/` na raiz do projeto, ao lado de `transcrições/`, destinado exclusivamente aos sumários consolidados das seções.

Estrutura esperada:

* `transcrições/`

  * `Seção 01/`
  * `Seção 02/`
  * ...
* `sumario/`

  * `Seção 01 - Sumário.md`
  * `Seção 02 - Sumário.md`
  * ...

Objetivo:

* Gerar ou atualizar um arquivo de sumário consolidado para uma seção específica do curso, reunindo de forma resumida os principais conceitos abordados nas aulas da seção.

Regra obrigatória:

* Sempre que o usuário solicitar a criação ou atualização de um sumário de seção, o arquivo deve ser criado ou atualizado dentro da pasta `sumario/`.
* O agente nunca deve criar ou alterar arquivos dentro da pasta `transcrições/`.

Comportamento esperado:

1. Identificar a seção indicada pelo usuário.
2. Localizar a pasta correspondente dentro de `transcrições/`.
3. Ler as transcrições das aulas pertencentes à seção.
4. Identificar os principais conceitos, temas e progressão lógica entre as aulas.
5. Criar ou atualizar o arquivo de sumário correspondente dentro de `sumario/`.

Regras de atualização:

* Se o arquivo de sumário da seção **não existir**, ele deve ser criado.
* Se o arquivo **já existir**, o agente deve atualizar o conteúdo preservando a estrutura existente quando possível e incorporando novas informações ou aulas que ainda não estejam no sumário.

Estrutura recomendada do sumário:

# Seção XX - Sumário

## Visão Geral da Seção

Breve explicação sobre o objetivo da seção e os principais conceitos abordados.

## Conceitos Principais

Lista dos conceitos importantes apresentados ao longo da seção.

## Resumo das Aulas

### [[01-001 Nome da Aula]]

Resumo curto do conteúdo principal da aula.

### [[01-002 Nome da Aula]]

Resumo curto do conteúdo principal da aula.

### [[01-003 Nome da Aula]]

Resumo curto do conteúdo principal da aula.

## Conexões Importantes

Relações entre os conceitos apresentados nas aulas da seção.

## Observações

Notas relevantes ou pontos importantes destacados pelo instrutor.

Referências obrigatórias:

* Cada aula mencionada no sumário deve ser referenciada utilizando o padrão de links do Obsidian: `[[Nome do Arquivo]]`.
* As referências devem apontar diretamente para os arquivos de transcrição dentro de `transcrições/`.

Exemplo:

### [[01-003 Introdução ao Data Lake]]

Nesta aula o instrutor apresenta os fundamentos de Data Lakes e explica como eles diferem de Data Warehouses.

Diretrizes adicionais:

* O sumário deve representar a progressão lógica da seção.
* As aulas devem aparecer no sumário na mesma ordem em que estão organizadas dentro da seção.
* Sempre utilizar os links `[[...]]` para conectar o sumário às transcrições.
* Nunca modificar os arquivos dentro de `transcrições/`.

Resultado esperado:

* Um arquivo consolidado em `sumario/` que funcione como uma visão geral navegável da seção dentro do Obsidian.
