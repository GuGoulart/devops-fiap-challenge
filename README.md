w# 🏍️ Mottu Challenge 2025 – DevOps (FIAP)

Repositório da solução desenvolvida para o **Challenge 2025** da FIAP, disciplina **DevOps Tools & Cloud Computing**. O projeto propõe uma API RESTful para mapeamento e gestão de motocicletas em pátios da empresa **Mottu**, utilizando ASP.NET Core, Docker e deploy em nuvem via Azure CLI.

## 👥 Integrantes

- Gustavo Goulart Bretas – RM555708
- Victor Nieves Britto Medeiros – RM554557
- Alice Teixeira Caldeira – RM556293

## 🛠️ Tecnologias Utilizadas

- ASP.NET Core 9.0
- Entity Framework Core + Oracle
- Docker
- Azure CLI
- Swagger (OpenAPI)
- Git/GitHub

## 📚 Descrição da Solução

A solução implementa:

- API RESTful para motos com operações CRUD.
- Integração com banco Oracle via EF Core.
- Conteinerização da aplicação com Docker.
- Deploy da aplicação em uma **VM Linux na Azure** via linha de comando.
- Documentação da API com Swagger.
- Repositório GitHub com README completo e scripts utilizados.

---

### ☁️ Deploy na Azure via CLI

No Shell Azure:

-Criação do Resource Group
az group create --name mottu-group --location eastus

-Criação da Máquina Virtual
az vm create \
--resource-group mottu-group \
--name mottu-vm \
--image Ubuntu2204 \
--size Standard_B1s \
--admin-username azureuser \
--generate-ssh-keys \
--public-ip-address mottu-vm-public-ip

-Abertura de Portas na VM
az vm open-port --resource-group mottu-group --name mottu-vm --port 80 --priority 1002
az vm open-port --resource-group mottu-group --name mottu-vm --port 8080 --priority 1003

-Consulta do IP da VM
az vm list-ip-addresses --resource-group mottu-group --name mottu-vm --output table

No Terminal:
-Acesso à Máquina via SSH
ssh -i C:\Users\gusta\.ssh\id_rsa azureuser@IpdaVM (o ip utilizado foi: 4.157.243.78)

-Instalação do Docker
sudo apt update
sudo apt install -y docker.io
sudo usermod -aG docker azureuser
newgrp Docker

-Docker - Build e Push da Imagem
docker build -t mochizuka/mottu-api .
docker push mochizuka/mottu-api

-Docker - Pull e Execução na VM
docker pull mochizuka/mottu-api
docker run -d -p 80:8080 mochizuka/mottu-api

-Como Rodar o Projeto Localmente
git clone https://github.com/GuGoulart/devops-fiap-challenge
cd mottu-api
dotnet build
dotnet run

---

📂 Links Importantes

🔗 GitHub: [https://github.com/seu-usuario/mottu-api](https://github.com/GuGoulart/devops-fiap-challenge)

📽️ Vídeo da entrega: [https://youtu.be/cyCjrkpXW7w](https://youtu.be/cyCjrkpXW7w?si=pDp2K7zhb8F6rlSs)
