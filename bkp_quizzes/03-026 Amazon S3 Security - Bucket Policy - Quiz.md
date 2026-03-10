---
sources:
  - "[[03-026 Amazon S3 Security - Bucket Policy]]"
---

> [!question] Qual é a maneira mais comum e recomendada atualmente para configurar a segurança baseada em recursos em um bucket do Amazon S3?
> a) Access Control Lists (ACLs) de Objetos
> b) Políticas de Bucket (Bucket Policies)
> c) Políticas locais da rede On-Premises
> d) Security Groups vinculados ao Bucket
>> [!success]- Answer
>> b) Políticas de Bucket (Bucket Policies)

> [!question] Quais dos seguintes componentes principais fazem parte da estrutura de um documento JSON de uma Bucket Policy?
> a) Effect
> b) Action
> c) Route
> d) Principal
> > [!success]- Answer
> > a) Effect
> > b) Action
> > d) Principal

> [!question] Se você precisa conceder acesso a um Bucket do Amazon S3 para uma instância EC2, qual é a abordagem correta e recomendada?
> a) Criar um usuário IAM e embutir as credenciais diretamente na instância EC2
> b) Utilizar uma Bucket Policy permitindo o endereço IP elástico da instância
> c) Criar uma função do IAM (IAM Role) com as permissões corretas e anexar à instância EC2
> d) Tornar o bucket totalmente público e acessá-lo anonimamente
> > [!success]- Answer
> > c) Criar uma função do IAM (IAM Role) com as permissões corretas e anexar à instância EC2

> [!question] Se uma política de Bucket (Bucket Policy) estiver configurada para permitir acesso público, mas a funcionalidade "Block Public Access" estiver ativada nas configurações do bucket, os objetos poderão ser acessados publicamente.
> > [!success]- Answer
> > False

> [!question] Quais são os principais cenários de uso para a implementação de S3 Bucket Policies?
> a) Conceder acesso aos buckets entre contas diferentes da AWS (Cross-account access)
> b) Compactar automaticamente arquivos de texto antes do upload
> c) Forçar a condição para que objetos sejam criptografados no momento do upload
> d) Fornecer acesso público aos objetos presentes no bucket
> > [!success]- Answer
> > a) Conceder acesso aos buckets entre contas diferentes da AWS (Cross-account access)
> > c) Forçar a condição para que objetos sejam criptografados no momento do upload
> > d) Fornecer acesso público aos objetos presentes no bucket

> [!question] Associação dos elementos de um documento JSON de uma Bucket Policy com suas funções:
> > [!example] Group A
> > a) Principal
> > b) Action
> > c) Resource
> > d) Effect
> > [!example] Group B
> > x) Define a chamada de API S3 que será permitida ou negada (ex: s3:GetObject).
> > y) Indica quem está recebendo a permissão ou negação (usuário, conta ou público com `*`).
> > z) Informa em quais buckets e objetos essa política se aplica através do ARN.
> > w) Determina ativamente se o acesso será Permitir (Allow) ou Negar (Deny).
> > [!success]- Answer
> > a) -> y)
> > b) -> x)
> > c) -> z)
> > d) -> w)

> [!question] Para permitir que um usuário IAM de **outra conta da AWS** acesse seus buckets S3 (cross-account acess), qual mecanismo primário deve ser utilizado?
> a) Amazon S3 Storage Lens
> b) Amazon EBS Volumes
> c) Bucket Policies
> d) Server-Side Encryption
> > [!success]- Answer
> > c) Bucket Policies
