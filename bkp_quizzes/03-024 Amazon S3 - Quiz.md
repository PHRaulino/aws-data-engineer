---
sources:
  - "[[03-024 Amazon S3]]"
---

Este quiz revisa os princípios básicos de armazenamento em objetos e a escalabilidade flexível do Amazon S3. A aula base, [[03-024 Amazon S3]], atua como fundação conceitual apresentada na progressão geral da [[Seção 03 - Sumário]].

> [!question] Qual é o tamanho máximo de um objeto que pode ser armazenado no Amazon S3?
> a) 5 Gigabytes
> b) 5 Terabytes
> c) 5 Petabytes
> d) Sem limite
> > [!success]- Answer
> > b) 5 Terabytes

> [!question] Considerando a nomenclatura dos buckets no Amazon S3, qual das seguintes regras é verdadeira?
> a) O nome do bucket possui letras maiúsculas para categorização
> b) O nome do bucket é único apenas dentro de cada região
> c) O nome do bucket deve ser globalmente exclusivo em todas as contas e regiões da AWS
> d) O nome pode começar com caracteres especiais ou underscores
> > [!success]- Answer
> > c) O nome do bucket deve ser globalmente exclusivo em todas as contas e regiões da AWS

> [!question] Como são denominados os arquivos que são armazenados dentro de um bucket do Amazon S3?
> > [!success]- Answer
> > Objetos

> [!question] Apesar do nome do bucket ser global, em que nível físico um bucket do Amazon S3 é efetivamente criado?
> > [!success]- Answer
> > Numa Região específica

> [!question] O Amazon S3 possui o conceito real de diretórios no seu backend (sistema hierárquico de pastas reais).
> > [!success]- Answer
> > False

> [!question] Dos casos de uso abaixo, quais são comumente e recomendavelmente atendidos pelo Amazon S3?
> a) Hospedagem de sites estáticos
> b) Execução do sistema operacional para instâncias EC2
> c) Data Lakes e big data
> d) Armazenamento para Disaster Recovery e Backups
> > [!success]- Answer
> > a, c, d

> [!question] Qual funcionalidade é exigida para realizar o upload de arquivos com tamanho superior a 5 Gigabytes no Amazon S3?
> > [!success]- Answer
> > Multi-part upload

> [!question] Associe os termos e definições de objetos do Amazon S3 com suas descrições correspondentes.
> > [!example] Group A
> > a) Object Key
> > b) Metadata
> > c) Tags
> > d) Prefix
>
> > [!example] Group B
> > n) Caminho com barras inserido antes do nome real do objeto (simulando pastas).
> > o) Até 10 pares Unicode de chave-valor utilizados para ciclo de vida e segurança.
> > p) Caminho completo do arquivo no bucket S3, sem usar diretórios reais.
> > q) Lista de pares de chave-valor definidos pelo sistema/usuário para informações do arquivo.
>
> > [!success]- Answer
> > a) -> p)
> > b) -> q)
> > c) -> o)
> > d) -> n)
