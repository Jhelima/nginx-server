# Projeto de Configuração de Servidores NGINX com Docker Compose

Este projeto configura múltiplos servidores NGINX usando Docker Compose. Inclui um servidor NGINX principal e três servidores adicionais (`nginx1`, `nginx2`, `nginx3`). O objetivo é demonstrar diferentes configurações e funcionalidades do NGINX, incluindo servidor web, proxy reverso, segurança com HTTPS e otimização de desempenho.

## Estrutura do Projeto

- `nginx-server`
  - `docker-compose.yml`
  - `html/` (Conteúdo web para o servidor NGINX principal)
  - `nginx/` (Configurações do NGINX)
  - `cert/` (Certificados SSL/TLS)
  - `html1/` (Conteúdo web para `nginx1`)
  - `html2/` (Conteúdo web para `nginx2`)
  - `html3/` (Conteúdo web para `nginx3`)

## Configurações dos Servidores

### Servidor Principal (`nginx`)

- **Imagem:** `nginx:1.25`
- **Portas:** 80 (HTTP) e 443 (HTTPS)
- **Volumes:**
  - `./html:/usr/share/nginx/html:ro` (Conteúdo web)
  - `./nginx:/etc/nginx` (Configurações do NGINX)
  - `./cert:/cert` (Certificados SSL/TLS)

### Servidores Adicionais

#### `nginx1`
- **Imagem:** `nginx:1.25`
- **Porta:** 81 (HTTP)
- **Volume:** `./html/html1:/usr/share/nginx/html:ro`

#### `nginx2`
- **Imagem:** `nginx:1.25`
- **Porta:** 82 (HTTP)
- **Volume:** `./html/html2:/usr/share/nginx/html:ro`

#### `nginx3`
- **Imagem:** `nginx:1.25`
- **Porta:** 83 (HTTP)
- **Volume:** `./html/html3:/usr/share/nginx/html:ro`

## Funcionalidades

### 1. Configuração Básica
Configure o NGINX para atuar como servidor web para um site ou aplicativo. O conteúdo web está localizado nos diretórios `html`, `html1`, `html2`, e `html3`.

### 2. Proxy Reverso
Configure regras de proxy reverso no NGINX para direcionar o tráfego para diferentes serviços ou aplicativos. Isso é feito através dos arquivos de configuração do NGINX no diretório `nginx`.

### 3. Segurança e HTTPS
Implemente HTTPS com certificados SSL/TLS armazenados no diretório `cert`. Configure políticas de segurança no NGINX para proteger o tráfego web.

### 4. Otimização de Desempenho
Aplique técnicas de otimização para melhorar o desempenho do `NGINX`, como cache de conteúdo estático, compressão gzip, e otimização de configuração.

## Instruções para Uso

### Passo 1: Clonar o Repositório

```sh
git clone https://github.com/Jhelima/nginx-server.git
```
```sh
cd nginx-server
```

### Passo 2: Inicializar os Contêineres
```sh
docker-compose up -d
```
#### Passo 3: Verificar os Serviços
Acesse os servidores nos seguintes URLs:

- Servidor Principal: http://localhost
- Servidor nginx1: http://localhost:81
- Servidor nginx2: http://localhost:82
- Servidor nginx3: http://localhost:83

## Passo 4: Configuração Adicional

Edite os arquivos de configuração no diretório nginx para personalizar as regras de proxy reverso, segurança e otimização conforme necessário.