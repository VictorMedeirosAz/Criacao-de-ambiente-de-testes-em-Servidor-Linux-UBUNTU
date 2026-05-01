# 🚀 Diário de Bordo: Criação do Lab de Infraestrutura

Este repositório documenta a ressurreição de um hardware antigo para fins de estudo em Sistemas de Informação, focando em Linux, Redes e Desenvolvimento.

## 💻 1. O Hardware (The Vintage Beast)
* **Modelo:** Acer Aspire 5920 (Aprox. 12 anos de idade).
* **Objetivo:** Servidor dedicado para testes de banco de dados (MySQL) e lógica em C#.
* **Sistema Operacional:** Ubuntu Server (Sem interface gráfica para máxima performance).

## 🛠️ 2. Etapas de Configuração (Passo a Passo)

### A. Estabilização de Rede (IP Fixo)
Para garantir que o servidor seja sempre encontrado no mesmo endereço, configurei o **Netplan**.
* **Arquivo:** `/etc/netplan/00-installer-config.yaml`
* **Interface:** `enp8s0` (Ethernet).
* **Configuração:** IP `192.168.1.10`, Gateway `192.168.1.1`, DNS `8.8.8.8`.
* **Comando de Teste:** `sudo netplan try` (segurança contra erros de sintaxe YAML).

### B. Gestão de Energia
Aprendizado do comando de encerramento seguro para evitar corrupção de dados:
* `sudo shutdown now`

### C. Versionamento e Segurança (Git & SSH)
Em vez de usar senhas comuns (bloqueadas pelo GitHub para terminais), configurei a **Criptografia Assimétrica**.
1. **Instalação:** `sudo apt install git`.
2. **Geração de Chave:** `ssh-keygen -t ed25519`.
3. **Autenticação:** Chave pública adicionada ao perfil do GitHub para permitir `git push` sem senha.

## 🧠 Notas Pessoais (TDAH Friendly)
* **Por que o IP Fixo?** Menos fricção. Não preciso caçar o IP toda vez que ligar o servidor.
* **Por que o SSH?** Segurança e agilidade. O terminal do Windows se comunica direto com o Linux.
* **Próximos Passos:** Instalar o ambiente .NET e MySQL.

🛡️ Implementação de Segurança: Criptografia Assimétrica (SSH)
Nesta etapa, elevamos o nível de segurança do laboratório substituindo a autenticação tradicional por senha pela autenticação baseada em chaves públicas.

1. O que foi feito e Utilidade
Foi gerado um par de chaves utilizando o algoritmo ED25519 (mais seguro e performático que o antigo RSA).

Utilidade: Isso impede ataques de "força bruta" (onde robôs tentam adivinhar sua senha milhares de vezes). Sem a chave privada física no meu computador principal, o acesso ao servidor é matematicamente impossível, mesmo que alguém descubra a senha do usuário.

2. Metodologia de Aplicação
O processo foi realizado seguindo o fluxo padrão de administração de sistemas Linux:

Geração no Host (Windows): Utilizado o comando ssh-keygen -t ed25519 para criar a identidade digital do computador de gestão.

Transferência de Identidade: Como o comando ssh-copy-id é nativo do Linux, foi utilizado um pipe no PowerShell para injetar a chave pública no arquivo ~/.ssh/authorized_keys do servidor remoto:

NO POWERSHELL: type $env:USERPROFILE\.ssh\id_ed25519.pub | ssh usuario@ip "cat >> .ssh/authorized_keys"

Endurecimento de Permissões (Hardening): Aplicadas permissões restritivas no servidor para garantir que apenas o proprietário possa ler as chaves autorizadas:

Pasta .ssh: chmod 700

Arquivo authorized_keys: chmod 600

3. Resultados Obtidos
Acesso Passwordless: Login imediato e seguro sem necessidade de digitação de credenciais.

Segurança Auditável: O servidor agora reconhece apenas dispositivos autorizados previamente através da troca de chaves.

---
*Atualizado em: 2026-05-01*# Criacao-de-ambiente-de-testes-em-Servidor-Linux-UBUNTO
Utilização de um Hardware antigo para aprofundar meus estudos sobre a utilização, administração e gerenciamento de um Servidor Ubunto Linux. 
