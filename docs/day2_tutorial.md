## Day2 - Backend em Node.js

#### Iniciando o projeto
- `mkdir backend` e `cd backend`
- `yarn init -y`
- `code .`
- No terminal do vscode:
  - `yarn add express`
  - o arquivo *yarn.lock* e o diretório *node_modules* serão gerados
  
#### Estrutura inicial do projeto
- *node_modules* possui as dependências do do yarn
- `mkdir src` e `cd src`
- crie o arquivo *server.js* com as configurações do servidor:
  - Inicializando o express (Micro Framework do Node.js)
  - Conectando com o MongoDB
  - Definindo o tipo de retorno da API
  - Definindo o arquivo de rotas
  - Especificando a porta
- no arquivo *routes.js* especifique as rotas da API e suas respectivas chamadas aos controllers
- rodando o server: `node src/server.js`

#### Habilitando o modo Dev
- instalando o *nodemon* como devDependencies: `yarn add nodemon -D`
- inserir esse trecho no arquivo *package.json*:
```js
  "scripts": {
    "dev": "nodemon src/server.js"
  },
```
- rodando o server: `yarn dev`
- cada alteração no código o servidor vai ser restartado novamente

#### Configurando o Insomnia
- https://insomnia.rest/download/#linux
- New environment -> Manage environments
```js
{
  "base_url": "http://localhost:3333"
}
```
#### Configurando MongoDB
- crie uma conta em: mongodb.com/cloud/atlas
- Build a cluster -> defina um nome -> Create cluster
- Na aba Database Access -> Add new user:
  - Selecione Read and Write any database -> Defina user e password -> Add user
- Na aba Network access -> Add IP address:
  - Selecione Allow access from anywhere -> Confirm
- Na aba Clusters -> Connect:
  - Selecione Connect your aplication -> Driver (Node.js) e Version (3.0 or later)
  - Copy na URL gerada
- Na aplicação:
  - `yarn add mongoose`
  - connect utilizando *mongoose* com URL (substituindo os dados do user) no *server.js*
- Testando o acesso a porta do MongoDB: portquiz.net/27017

#### Upload de arquivos com *Multer*
- `yarn add multer`
- fora do src: `mkdir uploads`
- em *src/config* crie o arquivo *upload.js* que ficará responsável por salvar os arquivos neste diretório

#### MVC
- sem a camada *views* já que é uma API
- *models*:
  - Representa uma entidade da aplicação
  - Uma tabela no banco de dados
  - Nome no singular em camelcase
  - Possui o Schema da entidade que será passado para o mongoose
- *controllers*:
  - Regras de negócio da aplicação
  - Receber a requisição, tratar e devolver uma resposta
  - pode conter os métodos: *index*, *show*, *store*, *update* e *destroy*
  
#### HTTP
- métodos: *GET*, *POST*, *PUT* e *DELETE*
- especificados nas rotas da aplicação
- cada chamada as rotas possuem uma *request* e *response*
- a *request* pode conter dados em:
  - **query**: para filtros
  - **params**: para edição e delete
  - **body**: para criação e edição
  
#### Mais informações
- https://nodejs.org/en/docs/
- https://expressjs.com/pt-br/
- https://mongoosejs.com/docs/
- https://github.com/expressjs/multer
- https://blog.mbeck.com.br/api-rest-e-os-verbos-http-46e189085e21

