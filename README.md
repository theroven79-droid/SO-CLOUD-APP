# ☁️ Relatório do projeto — SO Cloud App

## 📌 Visão geral

O **SO Cloud App** é uma aplicação didática de monitoramento básico, desenvolvida em **Node.js com Express**. Seu objetivo é consultar informações do sistema operacional em que o servidor está funcionando e apresentá-las em uma página HTML.

## 📂 Composição do projeto

| Arquivo ou pasta | Descrição |
|---|---|
| [`cloud-so-app.js`](cloud-so-app.js) | Implementação do servidor, da rota principal e da página com as informações do sistema. |
| [`package.json`](package.json) | Declara as dependências Express e CORS. |
| [`package-lock.json`](package-lock.json) | Registra as versões das dependências resolvidas pelo npm. |
| `node_modules/` | Contém dependências instaladas e incluídas no repositório. |

## 📊 Informações apresentadas

A aplicação atende à rota `GET /` e utiliza o módulo nativo `os` do Node.js para consultar:

| Informação | Função utilizada |
|---|---|
| Nome da máquina e plataforma | `os.hostname()` e `os.platform()` |
| Arquitetura do sistema | `os.arch()` |
| Memória total e livre | `os.totalmem()` e `os.freemem()` |
| Número de processadores lógicos | `os.cpus().length` |
| Tempo de atividade | `os.uptime()` |

Os valores de memória são divididos por 1.048.576 e arredondados. Embora a interface os identifique como **MB**, o cálculo corresponde a **MiB**. O tempo de atividade é apresentado em minutos.

## ⚙️ Execução resumida

Com Node.js e npm instalados, na raiz do repositório:

```bash
npm ci
node cloud-so-app.js
```

A página fica disponível em `http://localhost:3000`, salvo se a variável `PORT` definir outra porta. O arquivo `package.json` não possui um script `start`.

## 🔎 Considerações finais

O painel mostra informações **do servidor**, não do dispositivo que acessa a página. A consulta é realizada a cada carregamento; não há atualização automática, API JSON, autenticação ou banco de dados. A dependência CORS está declarada, mas não é utilizada no arquivo principal.

**Referências:** [módulo `os` do Node.js](https://nodejs.org/api/os.html) · [Express](https://expressjs.com/) · [Documentação de deploy no Render](https://render.com/docs/deploy-node-express-app).
