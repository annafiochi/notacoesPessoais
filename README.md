# Notações Pessoais

Este projeto é uma API RESTful desenvolvida em Node.js para gerenciar anotações pessoais. Ele utiliza o framework Express.js e o  Prisma para interagir com um banco de dados. A API permite criar, listar, atualizar e deletar anotações, com suporte a atributos como título, conteúdo, cor, e marcação de favorito.

## Estrutura do Projeto

A estrutura do projeto está organizada da seguinte forma:

### Descrição dos Arquivos

- **`.env`**: Contém a variável de ambiente `DATABASE_URL` que aponta para o banco de dados SQLite.
- **`.gitignore`**: Define os arquivos e diretórios que não devem ser versionados, como `node_modules` e `.env`.
- **`package.json`**: Configurações do projeto, incluindo dependências e scripts.
- **`prisma/`**: Diretório relacionado ao Prisma, contendo o esquema do banco de dados, cliente Prisma e migrações.
  - **`schema.prisma`**: Define o modelo de dados `Nota` e configura o banco de dados SQLite.
  - **`client.js`**: Inicializa o cliente Prisma para interagir com o banco de dados.
  - **`migrations/`**: Contém as migrações do banco de dados.
- **`src/`**: Diretório principal do código-fonte.
  - **`server.js`**: Configura o servidor Express e define as rotas.
  - **`controllers/`**: Contém a lógica dos controladores.
    - **`anotacaoController.js`**: Implementa as operações de CRUD para as anotações.
  - **`models/`**: Contém a lógica de interação com o banco de dados.
    - **`anotacaoModel.js`**: Define os métodos para acessar e manipular os dados no banco.
  - **`routes/`**: Define as rotas da API.
    - **`anotacaoRoutes.js`**: Configura as rotas para as operações de CRUD.

## Funcionalidades

A API oferece as seguintes funcionalidades:

1. **Listar todas as anotações**:
   - Método: `GET`
   - Endpoint: `/anotacao`
   - Retorna todas as anotações cadastradas no banco de dados.

2. **Criar uma nova anotação**:
   - Método: `POST`
   - Endpoint: `/anotacao`
   - Corpo da requisição:
     ```json
     {
       "titulo": "Título da anotação",
       "conteudo": "Conteúdo da anotação"
     }
     ```
   - Retorna a anotação criada.

3. **Atualizar uma anotação existente**:
   - Método: `PUT`
   - Endpoint: `/anotacao/:id`
   - Corpo da requisição:
     ```json
     {
       "titulo": "Novo título",
       "conteudo": "Novo conteúdo",
       "favorita": true,
       "cor": "azul"
     }
     ```
   - Retorna a anotação atualizada.

4. **Deletar uma anotação**:
   - Método: `DELETE`
   - Endpoint: `/anotacao/:id`
   - Retorna uma mensagem de sucesso ou erro.

## Banco de Dados

O banco de dados utilizado é o SQLite, configurado no arquivo [.env](http://_vscodecontentref_/11). O modelo de dados `Nota` é definido no arquivo [schema.prisma](http://_vscodecontentref_/12) e possui os seguintes campos:

- [id](http://_vscodecontentref_/13): Identificador único da anotação.
- [titulo](http://_vscodecontentref_/14): Título da anotação.
- [conteudo](http://_vscodecontentref_/15): Conteúdo da anotação.
- [favorita](http://_vscodecontentref_/16): Indica se a anotação é marcada como favorita.
- [cor](http://_vscodecontentref_/17): Cor associada à anotação.
- [criadaEm](http://_vscodecontentref_/18): Data de criação da anotação.
- [atualizadaEm](http://_vscodecontentref_/19): Data da última atualização da anotação.

## Migrações

As migrações do banco de dados estão localizadas no diretório [migrations](http://_vscodecontentref_/20). Elas incluem:

1. **`20250311171932_create_table`**: Criação inicial da tabela `tasks`.
2. **`20250327171938_degelo`**: Exclusão da tabela `tasks` e criação da tabela `notas`.

## Como Executar o Projeto

1. **Instale as dependências**:
   ```bash
   npm install
2. Configure o banco de dados: Certifique-se de que o arquivo .env está configurado corretamente com a URL do banco de dados.

3. Execute as migrações:
npx prisma migrate dev
4. Inicie o servidor:
npm run dev
5. Acesse a API: O servidor estará disponível em
http://localhost:4000.
