# Desafio: Automatizando Infraestrutura com AWS CloudFormation

## 1. Objetivo do Projeto
O objetivo deste desafio foi **aplicar os conhecimentos adquiridos em AWS CloudFormation** para criar uma infraestrutura automatizada, documentando cada etapa do processo. O foco principal foi criar **um bucket S3** e **uma role IAM** de forma segura, utilizando **CloudFormation**, e registrar todas as observações e prints no repositório.

Ao final do desafio, o repositório contém:
- Template CloudFormation (`template.yaml`) funcional.  
- Documentação detalhada do processo (este README).  
- Capturas de tela da execução no console AWS (`/images`).  

---

## 2. Recursos Criados
Durante o laboratório, utilizei os seguintes recursos da AWS:

1. **Bucket S3**
   - Criado com nome único global para evitar conflitos.
   - Configurado com `AccessControl: Private`.
   - Versionamento desligado (`Suspended`) para simplificação.

2. **Role IAM**
   - Nome: `${StackName}-S3AccessRole`.
   - Permissões limitadas para operar apenas no bucket criado:
     - `s3:GetObject`
     - `s3:PutObject`
     - `s3:ListBucket`
   - Pode ser assumida por EC2 (ou outro serviço se necessário).
   - Política inline limitada ao bucket criado, evitando acesso global.

> O template CloudFormation garante que todos os recursos sejam criados de forma **automática e replicável**.

---

## 3. Passo a Passo da Execução

### 3.1 Preparação
1. Fiz login na AWS Console.  
2. Verifiquei que minha conta tinha permissões suficientes para criar:
   - S3 Buckets  
   - IAM Roles  
   - CloudFormation Stacks  

### 3.2 Criação do Template
1. Criei o arquivo `template.yaml` contendo:
   - Parâmetro para nome do bucket (`BucketName`).  
   - Recursos: `MyS3Bucket` e `S3AccessRole`.  
   - Outputs para consultar ARN da Role e nome do bucket após execução.  

### 3.3 Criação da Stack
1. Acesse **CloudFormation → Create stack → With new resources (standard)**.  
2. Selecionei **Upload a template file** e enviei `template.yaml`.  
3. Nome da stack: `dio-cloudformation-challenge-jullia`.  
4. Preenchi parâmetros necessários (nome do bucket único).  
5. Cliquei **Create stack**.

### 3.4 Acompanhamento da Execução
1. Observei a aba **Events** para acompanhar a criação passo a passo.  
2. Confirmei os recursos criados em **Resources**.  
3. Verifiquei os outputs em **Outputs**:
   - Nome do bucket S3.  
   - ARN da Role IAM.  
4. Tirei capturas de tela de todas as etapas e salvei em `/images`.

### 3.5 Teste dos Recursos
- Validei a Role IAM e testei permissão de leitura/escrita no bucket (via console ou CLI).  
- Confirmei que a Role não tinha permissões extras fora do bucket.

### 3.6 Exclusão de Recursos
- Para evitar custos futuros, deletei a stack via CloudFormation → **Delete Stack**.  
- Isso removeu bucket e a role IAM criados.

---

## 4. Boas Práticas Observadas
- Sempre usar nomes **únicos globalmente** para S3 Buckets.  
- Evitar políticas globais (`*`) e limitar a Role apenas ao recurso necessário.  
- Documentar prints e logs de execução para referência futura.  
- Testar os recursos manualmente após a criação da stack.  
- Excluir stacks que não estão em uso para evitar cobranças.

---
## 5. Referências
- [AWS CloudFormation Getting Started](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/GettingStarted.html)  
- [AWS CloudFormation Template Reference](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-reference.html)  
- [GitHub Markdown Guide](https://guides.github.com/features/mastering-markdown/)  

---

## 7. Conclusão
Este desafio consolidou meu aprendizado em **CloudFormation**, **IAM** e **S3**, além de reforçar boas práticas de documentação técnica e versionamento de projetos no GitHub. A experiência permitiu **automatizar a criação de recursos** de forma segura e replicável, essencial para projetos de infraestrutura como código (IaC).

---

## 💬 Autor
**Jullia Karolina de Paula**
- 💻Estudante de Análise e Desenvolvimento de Sistemas 
- 📍Brasil
- 🔗Linkedin:(https://www.linkedin.com/in/jullia-karolina-de-paula-89a93a283/)
- 📧Email: julliakarolinadev@gmail.com | julliakarolinadepauladev@gmail.com
- Bootcamp Santander Code Girls 2025 - AWS - Desafio: *Implementando Infraestrutura Automatizada com AWS CloudFormation*

---
## ✨ Aprender é plantar: a colheita vem de cada pequeno comando executado com coragem. 🌱

