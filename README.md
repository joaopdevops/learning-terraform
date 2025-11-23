# AWS S3 Bucket - Terraform

Provisionamento automatizado de bucket S3 na AWS usando Infrastructure as Code (IaC).

## Pré-requisitos

- Terraform >= 1.5.0
- AWS CLI configurado com credenciais
- Conta AWS ativa

## Configuração inicial

```bash
# Clone o repositório
git clone https://github.com/joaopdevops/learning-terraform.git
cd learning-terraform

# Configure suas credenciais AWS (se ainda não fez)
aws configure
```

## Personalize o bucket

Edite o arquivo `bucket.tf` e altere o nome do bucket:

```terraform
resource "aws_s3_bucket" "bucket" {
  bucket = "seu-nome-unico-aqui"  # Altere para um nome único
}
```

> ⚠️ Nomes de bucket S3 devem ser únicos globalmente

## Como usar

```bash
# Inicializar o Terraform
terraform init

# Visualizar mudanças antes de aplicar
terraform plan -out=plan.out

# Aplicar as mudanças
terraform apply plan.out

# Verificar bucket criado
aws s3 ls | grep seu-nome-unico-aqui

# Destruir recursos (quando não precisar mais)
terraform destroy
```

## Recursos criados

- S3 Bucket: `first-tf-joaopdevops`

## Observações

Arquivos `.tfstate` e `plan.out` não devem ser commitados (contêm informações sensíveis).
