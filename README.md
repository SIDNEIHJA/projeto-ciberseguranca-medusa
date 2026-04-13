# 🔐 Projeto de Cibersegurança - Bootcamp Riachuelo

## 📌 Descrição

Este projeto tem como objetivo demonstrar, na prática, ataques de força bruta utilizando o sistema operacional Kali Linux e a ferramenta Medusa em ambientes vulneráveis controlados.

Foram realizados testes em serviços como FTP, aplicação web (DVWA) e SMB, com foco na identificação de falhas de autenticação e aplicação de medidas de mitigação.

---

## 🎯 Objetivos

* Simular ataques de força bruta
* Explorar vulnerabilidades reais em ambiente controlado
* Aplicar técnicas de enumeração e exploração
* Documentar os resultados obtidos
* Propor medidas de segurança

---

## 🖥️ Ambiente Utilizado

* Kali Linux (Máquina atacante)
* Metasploitable 2 (Máquina vulnerável)
* DVWA (Damn Vulnerable Web Application)
* VirtualBox (Ambiente de virtualização)

---

## 🌐 Configuração de Rede

As máquinas foram configuradas em modo **Host-Only**, garantindo isolamento do ambiente.

### Verificação de conectividade:

```bash
ip a
ifconfig
ping <IP_DO_ALVO>
```

---

## 🔓 Cenário 1: Ataque de Força Bruta em FTP

### 🔍 Identificação do serviço

```bash
nmap -p 21 <IP_DO_ALVO>
```

### 📂 Wordlist utilizada

* users.txt
* passwords.txt

### 🚀 Execução do ataque

```bash
medusa -h <IP_DO_ALVO> -u msfadmin -P passwords.txt -M ftp
```

### ✅ Resultado

Acesso obtido com credenciais válidas.

### 🔐 Mitigação

* Uso de senhas fortes
* Desativar FTP
* Utilizar SFTP
* Limitar tentativas de login

---

## 🌐 Cenário 2: Ataque em Aplicação Web (DVWA)

### 🔗 Acesso

```
http://<IP_DO_ALVO>/dvwa
```

### 🔑 Credenciais padrão

* usuário: admin
* senha: password

### ⚙️ Configuração

Nível de segurança ajustado para **LOW**

### 🚀 Teste realizado

Simulação de ataque de força bruta em formulário de login.

### ✅ Resultado

Possível identificação de credenciais fracas.

### 🔐 Mitigação

* Implementar CAPTCHA
* Autenticação em dois fatores (MFA)
* Limitar tentativas de login
* Monitoramento de acessos

---

## 🖧 Cenário 3: Ataque SMB (Password Spraying)

### 🔍 Enumeração de usuários

```bash
enum4linux <IP_DO_ALVO>
```

### 🚀 Execução do ataque

```bash
medusa -h <IP_DO_ALVO> -U users.txt -P passwords.txt -M smbnt
```

### ✅ Resultado

Identificação de usuários com senhas fracas.

### 🔐 Mitigação

* Política de senhas fortes
* Bloqueio de conta após tentativas falhas
* Monitoramento de logs

---

## 📊 Resultados Gerais

Os testes demonstraram que:

* Senhas fracas são facilmente exploráveis
* Serviços expostos aumentam o risco de invasão
* A falta de políticas de segurança facilita ataques

---

## 🛡️ Recomendações de Segurança

* Implementar senhas complexas
* Utilizar autenticação multifator (MFA)
* Monitorar logs de acesso
* Restringir serviços desnecessários
* Aplicar políticas de bloqueio de conta

---

## 🖼️ Evidências

As capturas de tela dos testes estão disponíveis na pasta:

```
/images
```

---

## 📂 Estrutura do Projeto

```
/projeto-ciberseguranca
│
├── README.md
├── /wordlists
│   ├── users.txt
│   └── passwords.txt
├── /images
│   └── (prints dos testes)
```

---

## 🧠 Conclusão

Este projeto reforça a importância da cibersegurança na proteção de sistemas. Através de simulações práticas, foi possível compreender como ataques simples podem comprometer sistemas mal configurados.

---

## ⚠️ Aviso Legal

Este projeto foi realizado exclusivamente para fins educacionais, em ambiente controlado e autorizado. Qualquer uso indevido dessas técnicas é de total responsabilidade do usuário.

---

