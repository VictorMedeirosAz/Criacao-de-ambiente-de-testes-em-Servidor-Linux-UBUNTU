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

---
*Atualizado em: 2026-04-28*# Criacao-de-ambiente-de-testes-em-Servidor-Linux-UBUNTO
Utilização de um Hardware antigo para aprofundar meus estudos sobre a utilização, administração e gerenciamento de um Servidor Ubunto Linux. 
