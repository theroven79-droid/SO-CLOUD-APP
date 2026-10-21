# ☁️ SO Cloud App — Monitor de sistemas operacionais

Aplicação web didática construída com **Node.js e Express** para apresentar informações da máquina em que o servidor está em execução. O objetivo é demonstrar o uso do módulo nativo `os` do Node.js na geração de uma página HTML.

## 📌 Funcionamento

Quando alguém acessa a rota `GET /`, o servidor consulta as informações disponíveis no sistema e retorna uma página com os resultados. **Os valores apresentados são do servidor, e não do dispositivo de quem acessa o site.**

A página não realiza atualizações automáticas: para obter uma nova leitura, é necessário recarregá-la.

## ✨ Informações apresentadas

| Informação | Origem no código |
|---|---|
| Nome da máquina | `os.hostname()` |
| Plataforma | `os.platform()` |
| Arquitetura | `os.arch()` |
| Memória total | `os.totalmem()` |
| Memória livre | `os.freemem()` |
| Quantidade de CPUs lógicas | `os.cpus().length` |
| Tempo de atividade | `os.uptime()` |

Os valores de memória são divididos por `1024²` e arredondados; embora a página utilize a indicação **MB**, esse cálculo corresponde a unidades de **MiB**. O tempo de atividade é convertido para minutos.

## 📂 Arquivos

| Arquivo | Finalidade |
|---|---|
| [`cloud-so-app.js`](cloud-so-app.js) | Implementação do servidor Express e geração do HTML. |
| [`package.json`](package.json) | Dependências declaradas: Express e CORS. |
| [`package-lock.json`](package-lock.json) | Versões de dependências registradas pelo npm. |

A dependência `cors` consta em `package.json`, mas não é utilizada no arquivo principal.

## ⚙️ Instalação e execução

**Pré-requisitos:** Node.js e npm instalados. Na raiz do repositório:

```bash
npm ci
node cloud-so-app.js
```

Acesse **http://localhost:3000** no navegador.

Para utilizar outra porta em Bash:

```bash
PORT=3002 node cloud-so-app.js
```

O arquivo `package.json` não define um script `start`, portanto `npm start` não é o comando previsto para este projeto.

## 🌐 Rota disponível

| Método | Caminho | Resposta |
|---|---|---|
| `GET` | `/` | Página HTML com as informações do sistema. |

Para consultar a resposta via terminal:

```bash
curl http://localhost:3000/
```

## ☁️ Execução em serviços de nuvem

É possível configurar um serviço Node.js com `npm ci` como comando de instalação e `node cloud-so-app.js` como comando de inicialização. A aplicação lê a variável de ambiente `PORT` ou utiliza a porta 3000 por padrão.

Essas são orientações de configuração; **não comprovam que o projeto esteja publicado**.

## ⚠️ Limitações

Não há API JSON, autenticação, banco de dados, testes automatizados declarados nem atualização contínua no navegador.

**Referências:** [código do servidor](cloud-so-app.js) · [Node.js — módulo `os`](https://nodejs.org/api/os.html).
