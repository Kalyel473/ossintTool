<div align="center">

```
  ██████╗ ███████╗██╗███╗   ██╗████████╗ ██████╗  ██████╗ ██╗
 ██╔═══██╗██╔════╝██║████╗  ██║╚══██╔══╝██╔═══██╗██╔══██╗██║
 ██║   ██║███████╗██║██╔██╗ ██║   ██║   ██║   ██║██║  ██║██║
 ██║   ██║╚════██║██║██║╚██╗██║   ██║   ██║   ██║██║  ██║██║
 ╚██████╔╝███████║██║██║ ╚████║   ██║   ╚██████╔╝██████╔╝███████╗
  ╚═════╝ ╚══════╝╚═╝╚═╝  ╚═══╝   ╚═╝    ╚═════╝ ╚═════╝ ╚══════╝
```

**OSINTool v4.0** — Ferramenta Profissional de Coleta de Inteligência de Fontes Abertas

[![Bash](https://img.shields.io/badge/Shell-Bash-4EAA25?style=flat-square&logo=gnu-bash&logoColor=white)](https://www.gnu.org/software/bash/)
[![License](https://img.shields.io/badge/Licença-MIT-blue?style=flat-square)](LICENSE)
[![Version](https://img.shields.io/badge/Versão-4.0-cyan?style=flat-square)]()
[![Platform](https://img.shields.io/badge/Plataforma-Linux-orange?style=flat-square&logo=linux&logoColor=white)]()

</div>

---

## 📖 Visão Geral

O **OSINTool v4.0** é uma ferramenta completa de OSINT (*Open Source Intelligence*) desenvolvida em Bash, voltada para profissionais de segurança da informação, pesquisadores e investigadores digitais. Ela automatiza a coleta, correlação e exportação de dados provenientes de dezenas de fontes públicas, cobrindo domínios, e-mails, IPs, usernames, números de telefone, endereços de criptomoedas e muito mais.

### Principais Destaques

- **12 módulos independentes** de reconhecimento e coleta
- **Exportação automática** em HTML interativo, CSV e log completo
- **Integração com APIs** profissionais (Shodan, VirusTotal, HIBP, Censys e outras)
- **Modo silencioso (CLI)** para automação e pipelines
- **Relatório HTML** estilizado com design cyberpunk, pronto para apresentação

---

## 📋 Índice

- [Módulos Disponíveis](#-módulos-disponíveis)
- [Requisitos](#-requisitos)
- [Instalação](#-instalação)
- [Configuração de APIs](#-configuração-de-apis)
- [Como Usar](#-como-usar)
- [Exemplos de Uso](#-exemplos-de-uso)
- [Saída e Relatórios](#-saída-e-relatórios)
- [Aviso Legal](#-aviso-legal)

---

## 🧩 Módulos Disponíveis

| # | Módulo | Descrição | Fontes Utilizadas |
|---|--------|-----------|-------------------|
| 1 | 🌐 **Domínio** | DNS, WHOIS, subdomínios, SSL/TLS, Wayback Machine | crt.sh, HackerTarget, Amass, Sublist3r, SecurityTrails, Shodan |
| 2 | 📧 **E-mail** | Verificação de vazamentos, Gravatar, pastebins, validação MX | HIBP, Hunter.io, Gravatar, theHarvester |
| 3 | 🌍 **IP** | Geolocalização, ASN, reputação, TOR check, serviços expostos | IPInfo, AbuseIPDB, GreyNoise, Shodan, Censys, VirusTotal |
| 4 | 👤 **Username** | Busca em 40+ redes sociais e plataformas | GitHub, Instagram, LinkedIn, TikTok, Reddit, Steam, Spotify e mais |
| 5 | 🔌 **Port Scan** | Scan de portas com detecção de serviços e vulnerabilidades | Nmap (NSE scripts), Masscan |
| 6 | 📄 **Metadados** | Extração de EXIF, GPS, PDF, HTML e comentários ocultos | ExifTool, análise local |
| 7 | 📱 **Telefone** | Validação, operadora, WhatsApp check | NumVerify, Truecaller (manual) |
| 8 | 🛡️ **CVE / Vuln** | Busca por CVEs e exploits por ID ou palavra-chave | NVD (NIST), ExploitDB / SearchSploit |
| 9 | ₿ **Crypto** | Análise de carteiras Bitcoin, Ethereum e Litecoin | Blockchain.info, Etherscan |
| 10 | 🔎 **Google Dorks** | Geração de dorks avançados para diversas finalidades | — (geração local) |
| 11 | 🏢 **Empresa** | OSINT corporativo, infraestrutura e funcionários | Shodan, theHarvester, sugestões manuais |
| 12 | 🌐 **HTTP Headers** | Análise de cabeçalhos de segurança e tecnologias expostas | curl (análise local) |

---

## ⚙️ Requisitos

### Obrigatórios

| Ferramenta | Instalação |
|------------|-----------|
| `bash` (≥ 4.0) | Padrão na maioria das distros Linux |
| `curl` | `apt install curl` |
| `jq` | `apt install jq` |
| `whois` | `apt install whois` |
| `dig` | `apt install dnsutils` |
| `host` | `apt install dnsutils` |
| `nmap` | `apt install nmap` |
| `exiftool` | `apt install libimage-exiftool-perl` |
| `python3` | `apt install python3` |
| `openssl` | `apt install openssl` |

### Opcionais (ampliam funcionalidades)

| Ferramenta | Uso no OSINTool |
|------------|----------------|
| `amass` | Enumeração passiva de subdomínios |
| `sublist3r` | Enumeração de subdomínios |
| `whatweb` | Detecção de tecnologias web |
| `nikto` | Scan de vulnerabilidades web |
| `sslscan` | Análise de vulnerabilidades SSL/TLS |
| `theHarvester` | Coleta de e-mails e metadados |
| `masscan` | Scan ultra-rápido de todas as portas (requer root) |
| `searchsploit` | Busca no ExploitDB |
| `traceroute` | Rastreamento de rota de rede |
| `dnsx` / `httpx` | Resolução e probing de subdomínios |

---

## 🚀 Instalação

### 1. Clonar o repositório

```bash
git clone https://github.com/kalyel473/osinttool.git
cd osinttool
```

### 2. Conceder permissão de execução

```bash
chmod +x osinttool.sh
```

### 3. Instalar dependências obrigatórias (Debian/Ubuntu)

```bash
sudo apt update && sudo apt install -y \
  curl jq whois dnsutils nmap \
  libimage-exiftool-perl python3 openssl
```

### 4. (Opcional) Instalar ferramentas adicionais

```bash
# Amass
go install -v github.com/owasp-amass/amass/v4/...@master

# Sublist3r
pip3 install sublist3r

# WhatWeb
sudo apt install whatweb

# Nikto
sudo apt install nikto

# sslscan
sudo apt install sslscan

# theHarvester
pip3 install theHarvester

# Masscan (requer root para execução)
sudo apt install masscan

# SearchSploit (ExploitDB)
sudo apt install exploitdb
```

---

## 🔑 Configuração de APIs

O OSINTool funciona sem chaves de API, mas ativá-las expande significativamente os resultados. Configure pelo menu interativo (opção `15`) ou edite o arquivo `.osintool_config` manualmente:

```bash
./osinttool.sh
# Selecione a opção 15 → Configurar APIs
```

Ou edite diretamente:

```bash
nano .osintool_config
```

### APIs Suportadas

| API | Gratuita? | Cadastro |
|-----|-----------|---------|
| **Shodan** | Limitada | [account.shodan.io](https://account.shodan.io/register) |
| **Have I Been Pwned (HIBP)** | Paga | [haveibeenpwned.com](https://haveibeenpwned.com/API/Key) |
| **VirusTotal** | Limitada | [virustotal.com](https://www.virustotal.com) |
| **AbuseIPDB** | Limitada | [abuseipdb.com](https://www.abuseipdb.com/api) |
| **IPInfo** | Limitada | [ipinfo.io](https://ipinfo.io/signup) |
| **SecurityTrails** | Limitada | [securitytrails.com](https://securitytrails.com) |
| **GreyNoise** | Limitada | [greynoise.io](https://greynoise.io) |
| **Hunter.io** | Limitada | [hunter.io](https://hunter.io/api) |
| **Censys** | Limitada | [censys.io](https://censys.io/register) |
| **NumVerify** | Limitada | [numverify.com](https://numverify.com) |

> As chaves são salvas localmente em `.osintool_config`. **Nunca compartilhe este arquivo.**

---

## 💻 Como Usar

### Modo Interativo (Menu)

```bash
./osinttool.sh
```

Exibe o menu principal com todas as opções numeradas. Ideal para uso manual e exploração.

### Modo CLI (Linha de Comando)

Execute módulos diretamente via argumentos, sem passar pelo menu:

```
Uso: ./osinttool.sh [opção] [alvo]

  -d, --domain    <domínio>     Reconhecimento de domínio
  -e, --email     <email>       OSINT de e-mail
  -i, --ip        <ip>          Inteligência de IP
  -u, --username  <username>    Busca em redes sociais
  -p, --portscan  <ip/domínio>  Scan de portas
  -m, --metadata  <url|arquivo> Extração de metadados
  -ph,--phone     <número>      OSINT de telefone
  -c, --cve       <CVE|soft>    Busca de CVE/vulnerabilidades
  -cr,--crypto    <endereço>    Análise de carteira crypto
  -dk,--dorks     <alvo>        Geração de Google Dorks
  -co,--company   <empresa>     OSINT corporativo
  -hh,--headers   <url>         Análise de headers HTTP
  -f, --full      <alvo>        Relatório completo automático
  -s, --silent    <alvo>        Modo silencioso (só exporta arquivo)
  -h, --help                    Exibe esta ajuda
```

---

## 📌 Exemplos de Uso

```bash
# Reconhecimento completo de um domínio
./osinttool.sh --domain exemplo.com.br

# Verificar se um e-mail aparece em vazamentos
./osinttool.sh --email usuario@gmail.com

# Inteligência sobre um IP suspeito
./osinttool.sh --ip 45.33.32.156

# Buscar username em 40+ plataformas
./osinttool.sh --username josesilva123

# Scan de portas com detecção de vulnerabilidades
./osinttool.sh --portscan 192.168.1.1

# Extrair metadados (GPS, autor, software) de uma imagem online
./osinttool.sh --metadata https://site.com/foto.jpg

# Buscar detalhes sobre um CVE
./osinttool.sh --cve CVE-2021-44228

# Verificar histórico de uma carteira Bitcoin
./osinttool.sh --crypto 1A1zP1eP5QGefi2DMPTfTL5SLmv7Divf

# Gerar dorks para um domínio
./osinttool.sh --dorks meusite.com

# Relatório completo com exportação HTML + CSV
./osinttool.sh --full alvo.com

# Modo silencioso para automação / pipelines
./osinttool.sh --silent alvo.com
```

---

## 📁 Saída e Relatórios

Todos os arquivos são salvos automaticamente em `./osint_results/`:

```
osint_results/
├── osint_report_YYYYMMDD_HHMMSS.html   ← Relatório visual interativo
├── osint_report_YYYYMMDD_HHMMSS.csv    ← Dados estruturados para análise
└── osintool_YYYYMMDD_HHMMSS.log        ← Log completo da execução
```

### Relatório HTML

O relatório HTML gerado é totalmente estático (sem dependências externas em runtime) e inclui:

- Índice de navegação por seções
- Dados organizados em cards e grids
- Codificação por cores para severidade (verde / amarelo / vermelho)
- Trechos de código formatados
- Links diretos para fontes e perfis encontrados

---

## 🔧 Estrutura do Projeto

```
osinttool/
├── osinttool.sh          ← Script principal
├── .osintool_config      ← Chaves de API (gerado automaticamente, não commitar)
├── osint_results/        ← Saída dos relatórios (gerado automaticamente)
└── README.md
```

---

## ⚠️ Aviso Legal

> **Este software destina-se exclusivamente a fins educacionais, de pesquisa e testes autorizados de segurança.**
>
> O uso desta ferramenta contra sistemas, redes ou indivíduos sem autorização explícita pode constituir violação de leis locais e internacionais, incluindo a **Lei Geral de Proteção de Dados (LGPD)**, o **Marco Civil da Internet** e legislações de crimes cibernéticos.
>
> **O autor não se responsabiliza por qualquer uso indevido desta ferramenta.**
>
> Use com responsabilidade. Obtenha sempre autorização prévia antes de realizar qualquer varredura ou coleta de dados sobre terceiros.

---

## 🤝 Contribuições

Contribuições são bem-vindas! Para reportar bugs, sugerir melhorias ou adicionar novos módulos:

1. Faça um fork do repositório
2. Crie uma branch: `git checkout -b feature/novo-modulo`
3. Commit suas mudanças: `git commit -m 'feat: adiciona módulo X'`
4. Envie um Pull Request

---

<div align="center">
  <sub>Desenvolvido para uso ético em segurança da informação · OSINTool v4.0</sub>
</div>
