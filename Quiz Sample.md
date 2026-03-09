---
sources:
  - "[[10-209 Key Salting]]"
---
> [!question] Qual é a prática de segurança recomendada para armazenar senhas de forma mais segura?
> a) Apenas armazenar as senhas sem nenhum sal
> b) Utilizar o mesmo valor de sal para todos os usuários
> c) Alternar periodicamente os valores de sal
> d) Compartilhar os valores de sal publicamente
>> [!success]- Answer
>> c) Alternar periodicamente os valores de sal

> [!question] O conceito de salting refere-se a adicionar um valor ____ aos dados antes de realizar o hash.
>> [!success]- Answer
>> aleatório

> [!question] Descreva como a técnica de salting pode ajudar a proteger as informações de usuários em um sistema.
>> [!success]- Answer
>> A técnica de salting contribui para a proteção das informações dos usuários ao adicionar um valor aleatório e exclusivo aos dados antes de criptografá-los. Isso impede a correspondência de senhas comuns a hashes pré-computados, dificultando a decodificação das senhas. Além disso, garantir que cada usuário tenha seu próprio valor de sal único fortalece a segurança, tornando mais desafiador para invasores decifrarem as senhas. A prática de alternar periodicamente os valores de sal aumenta ainda mais a proteção dos dados armazenados.

> [!question] Relacione os termos às suas definições correspondentes.
>> [!example] Group A
>> a) Ataques de tabela arco-íris
>> b) Salgar chaves
>> c) Valor de sal
>
>> [!example] Group B
>> n) Processo de usar lista de senhas existentes para comparar com hashes e obter senhas correspondentes
>> o) Informação aleatória adicionada aos dados antes do hash para proteção
>> p) Adicionar um valor aleatório único aos dados antes de aplicar o hash
>
>> [!success]- Answer
>> a) -> n)
>> b) -> p)
>> c) -> o)

> [!question] Explique a importância da salga de chaves na segurança das senhas.
>> [!success]- Answer
>> A salga de chaves é crucial na segurança das senhas pois adiciona um valor aleatório único aos dados antes de criptografá-los, o que impede ataques de tabela arco-íris. Isso garante que senhas idênticas não produzam o mesmo hash devido ao valor de sal exclusivo. Utilizando sais criptograficamente seguros e únicos para cada usuário, é possível evitar a decodificação das senhas armazenadas, aumentando significativamente a proteção dos dados pessoais.

> [!question] Quais são as práticas corretas relacionadas à salga de chaves? Selecione todas as opções corretas.
> a) Utilizar valores de sal exclusivos para cada usuário
> b) Compartilhar o mesmo valor de sal entre todos os usuários
> c) Garantir que os sais sejam criptograficamente seguros e aleatórios
> d) Alternar os valores de sal raramente
>> [!success]- Answer
>> a) Utilizar valores de sal exclusivos para cada usuário
>> c) Garantir que os sais sejam criptograficamente seguros e aleatórios

> [!question] A técnica de salgar chaves é usada para evitar ataques de tabela arco-íris.
>> [!success]- Answer
>> True

