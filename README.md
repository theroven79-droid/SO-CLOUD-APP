# SO Cloud App — Monitor de Sistemas Operacionais

Aplicação Node.js com Express que apresenta informações do sistema operacional em uma página HTML. A implementação está no arquivo [cloud-so-app.js](cloud-so-app.js).

Os dados são consultados quando a página é acessada. Para obter uma nova leitura, recarregue a página. As informações pertencem à máquina que executa o servidor Node.js.

## Conteúdo do repositório

| Arquivo | Conteúdo |
| --- | --- |
| [cloud-so-app.js](cloud-so-app.js) | Servidor Express, rota da página e leitura das informações do sistema. |
| [package.json](package.json) | Dependências declaradas: Express e CORS. |
| [package-lock.json](package-lock.json) | Versões das dependências registradas pelo npm. |

## Instalação e execução

Com Node.js e npm disponíveis, execute na raiz do repositório:

```bash
npm ci
node cloud-so-app.js
```

O programa imprime `Servidor rodando` ao iniciar e usa a porta **3000** por padrão. Para definir outra porta em um terminal Bash:

```bash
PORT=3002 node cloud-so-app.js
```

O [package.json](package.json) não define scripts de execução; por isso, o comando de inicialização é `node cloud-so-app.js`.

## Informações da página

A rota `GET /` retorna uma página com o título **Monitor de Sistemas Operacionais** e os seguintes campos:

| Campo | Informação exibida |
| --- | --- |
| Hostname | Nome da máquina, obtido por `os.hostname()`. |
| Plataforma | Plataforma do sistema, obtida por `os.platform()`. |
| Arquitetura | Arquitetura do processo, obtida por `os.arch()`. |
| Memória total | Valor de `os.totalmem()` dividido por 1024², arredondado e exibido com o rótulo MB. |
| Memória livre | Valor de `os.freemem()` dividido por 1024², arredondado e exibido com o rótulo MB. |
| CPUs | Quantidade de entradas retornadas por `os.cpus()`. |
| Uptime | Tempo de atividade do sistema convertido para minutos e arredondado. |

As consultas ao sistema usam o módulo nativo `os` do Node.js. A porta é lida de `process.env.PORT`, com o valor 3000 como padrão.

## Conferir a resposta

Com o processo em execução, faça uma requisição local em outro terminal:

```bash
curl --fail --silent http://127.0.0.1:3000/
```

A resposta deve conter o título do monitor e os campos da tabela. Se tiver definido outra porta, ajuste o comando.

## Observações

- O pacote CORS está declarado como dependência, mas não é utilizado em `cloud-so-app.js`.
- A implementação contém uma única rota, `GET /`, que retorna HTML.
- O `package.json` não define uma etapa de compilação nem um script de testes.
