# 📘 Insights do Desafio AWS CloudFormation

Este documento reúne minhas anotações, reflexões e aprendizados durante a implementação da primeira stack com AWS CloudFormation.

---

## 🛠️ Etapas Realizadas
- Criação da VPC e Subnet pública.
- Configuração do Internet Gateway e tabela de rotas.
- Definição de Security Group com regras de SSH e HTTP.
- Provisionamento da instância EC2 com Amazon Linux 2023.
- Instalação automática do Apache via UserData.
- Teste de acesso ao servidor web pelo PublicDNS.

---

## ✅ Aprendizados
- **Infraestrutura como Código (IaC):** percebi como o CloudFormation simplifica a replicação de ambientes.
- **Parametrização:** usar parâmetros como `InstanceType` e `KeyName` torna o template reutilizável.
- **UserData:** automatizar a instalação de pacotes economiza tempo e garante consistência.
- **Outputs:** muito úteis para obter rapidamente informações como IP público e URL do servidor.

---

## ⚠️ Dificuldades
- Ajustar a indentação correta do YAML (erros de formatação quebram a stack).
- Encontrar o **AMI ID** correto para a região (resolver via SSM Parameter Store foi a solução).
- Entender a ordem de dependência entre recursos (ex.: Internet Gateway precisa ser anexado antes da rota).

---

## 💡 Boas Práticas
- Versionar templates no GitHub com commits descritivos.
- Documentar cada recurso com comentários no YAML.
- Usar nomes claros para stacks e recursos.
- Validar o template antes de aplicar:
  ```bash
  aws cloudformation validate-template --template-body file://ec2-apache.yaml
