# SO Cloud App — Monitor de Sistemas Operacionais

Aplicação Node.js com Express que responde a uma requisição HTTP com uma página HTML contendo informações do sistema onde o servidor está em execução.

## O que a página apresenta

A rota definida em [cloud-so-app.js](cloud-so-app.js) consulta o módulo nativo `os`:

| Campo | Origem e formato |
|---|---|
| Hostname | `os.hostname()` |
| Plataforma | `os.platform()` |
| Arquitetura | `os.arch()` |
| Memória total e livre | Bytes de `os.totalmem()` e `os.freemem()`, divididos por 1024² e arredondados; a página usa o rótulo MB |
| CPUs | Quantidade de entradas de `os.cpus()` |
| Uptime | `os.uptime()` convertido em minutos e arredondado |

Os dados são obtidos a cada acesso à página. Não há atualização automática no navegador: recarregue a página para consultar novamente. As informações pertencem à máquina que executa o Node.js, inclusive quando ela está em nuvem.

## Arquivos do projeto

| Arquivo | Função |
|---|---|
| [cloud-so-app.js](cloud-so-app.js) | Servidor Express, rota HTML e chamada de inicialização. |
| [package.json](package.json) | Dependências declaradas: `express` e `cors`. |
| [package-lock.json](package-lock.json) | Resolução das dependências npm. |

O pacote `cors` está declarado, mas não é importado nem ativado pelo código atual.

## Instalação e execução

Com Node.js e npm disponíveis, execute na raiz:

```bash
npm ci
node cloud-so-app.js
```

O servidor usa a porta 3000 por padrão e imprime `Servidor rodando` quando inicia. O manifesto não define scripts npm; use o comando `node cloud-so-app.js` diretamente.

Para escolher outra porta em um terminal Bash:

```bash
PORT=3002 node cloud-so-app.js
```

A única variável lida pelo aplicativo é `PORT`, com fallback para 3000. O arquivo não carrega `.env` por conta própria.

## Rota HTTP

| Método e caminho | Resposta |
|---|---|
| `GET /` | HTML com o título “Monitor de Sistemas Operacionais” e as informações listadas acima. |

O projeto não define API JSON, rota própria de saúde, autenticação ou armazenamento em banco. Não há etapa de build nem suíte de testes declarada.

## Verificar a execução

Com o processo em execução, faça uma requisição local em outro terminal:

```bash
curl --fail --silent http://127.0.0.1:3000/
```

A resposta deve conter o título do monitor e os campos Hostname, Plataforma, Arquitetura, Memória Total, Memória Livre, CPUs e Uptime. Se usar outra porta, ajuste o comando.

As descrições deste guia são baseadas exclusivamente no código e nos manifests deste repositório.
