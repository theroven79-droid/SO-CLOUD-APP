# ☁️ SO Cloud App

O **SO Cloud App** é uma aplicação simples para visualizar informações do sistema operacional por meio de uma página web. Desenvolvido como exercício de **Node.js e Express**, o projeto conecta o funcionamento de um servidor HTTP à consulta de recursos da máquina em que ele está executando.

## 🖥️ O que aparece na página

Quando a rota principal (`/`) é acessada, o servidor consulta o módulo nativo `os` do Node.js e apresenta:

| Informação | O que representa |
|---|---|
| **Hostname** | Nome da máquina que executa a aplicação. |
| **Plataforma e arquitetura** | Identificação do sistema e da arquitetura utilizada. |
| **Memória total e livre** | Quantidade de memória disponível e capacidade informada pelo sistema. |
| **CPUs** | Número de processadores lógicos identificados. |
| **Uptime** | Tempo de atividade da máquina, exibido em minutos. |

As informações refletem o **ambiente do servidor** — seja ele local ou hospedado na nuvem.

## 🛠️ Tecnologias

| Tecnologia | Uso no projeto |
|---|---|
| **JavaScript / Node.js** | Execução do servidor e leitura das informações do sistema. |
| **Express** | Criação da rota HTTP que devolve a página. |
| **HTML** | Apresentação dos indicadores ao navegador. |

## 📂 Arquivos principais

- [`cloud-so-app.js`](cloud-so-app.js) — reúne a rota web e a consulta às informações do sistema.
- [`package.json`](package.json) — declara as dependências npm do projeto.
- [`package-lock.json`](package-lock.json) — registra as versões resolvidas dessas dependências.
- `node_modules/` — contém os pacotes instalados e seus arquivos de documentação originais.

## ▶️ Executando localmente

Com o Node.js e o npm instalados, utilize os comandos na raiz do repositório:

```bash
npm ci
node cloud-so-app.js
```

Acesse **http://localhost:3000**. O servidor utiliza a porta definida em `PORT` quando essa variável de ambiente está configurada.

## 🔗 Materiais de referência

[Node.js — módulo `os`](https://nodejs.org/api/os.html) · [Express](https://expressjs.com/) · [Render — hospedagem de aplicações Node.js](https://render.com/docs/deploy-node-express-app)
