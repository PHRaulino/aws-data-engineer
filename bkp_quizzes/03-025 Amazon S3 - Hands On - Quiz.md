---
sources:
  - "[[03-025 Amazon S3 - Hands On]]"
---

> [!question] Sobre os nomes dos buckets no Amazon S3, qual regra é obrigatória?
> a) O nome deve ser exclusivo apenas dentro da região selecionada.
> b) O nome deve ser exclusivo apenas dentro da conta AWS do usuário.
> c) O nome do bucket deve ser exclusivo globalmente, considerando todas as contas AWS e todas as regiões.
> d) O nome pode ser duplicado, desde que esteja em regiões diferentes da AWS.
> > [!success]- Answer
> > c) O nome do bucket deve ser exclusivo globalmente, considerando todas as contas AWS e todas as regiões.

> [!question] Ao criar um novo bucket, qual é a configuração recomendada de "Propriedade do Objeto" por motivos de segurança?
> > [!success]- Answer
> > ACL desativada

> [!question] Por que o botão "Abrir" no console permite visualizar um objeto no S3, enquanto acessar a "URL do objeto" retorna "Access Denied" por padrão?
> > [!success]- Answer
> > O botão "Abrir" utiliza uma URL pré-assinada (pre-signed URL) que inclui credenciais autorizadas temporárias. A "URL do objeto" tenta um acesso público, que é bloqueado pela configuração padrão do bucket.

> [!question] Verdadeiro ou Falso: No console da AWS, todos os buckets de uso geral, mesmo sendo criados em diferentes regiões, são exibidos em uma única visualização global do Amazon S3.
> > [!success]- Answer
> > True

> [!question] Associe as formas de acesso aos objetos com suas características explicadas no laboratório do Amazon S3:
> > [!example] Group A
> > a) URL pré-assinada (Pre-signed URL)
> > b) URL Pública (Object URL)
> > [!example] Group B
> > x) Retorna "Access Denied" por padrão, pois o bloqueio de acesso público está ativado na criação do bucket.
> > y) Permite a visualização do arquivo utilizando credenciais de segurança do usuário logado na AWS.
> > [!success]- Answer
> > a) -> y)
> > b) -> x)

> [!question] Quais das seguintes configurações costumam ser aplicadas ou recomendadas por padrão para garantir a segurança no momento em que criamos um bucket S3 pela interface? (Múltiplas corretas)
> a) ACL ativada
> b) Bloquear todo acesso público (ativado)
> c) Controle de versão habilitado no primeiro instante
> d) Criptografia com chave gerenciada do Amazon S3 (ativada)
> > [!success]- Answer
> > b, d

> [!question] Qual estrutura visual o Amazon S3 fornece no console para agrupar objetos, tornando a experiência semelhante à de plataformas como Google Drive e Dropbox?
> > [!success]- Answer
> > Pastas
