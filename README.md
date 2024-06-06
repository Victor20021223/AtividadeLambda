*-Documentação da API de Gerenciamento de Usuários-*

*Visão Geral*
Esta API permite o gerenciamento de dados de usuários utilizando o AWS DynamoDB como backend. Suporta operações para criar um novo usuário e recuperar detalhes de usuários com base no ID do usuário.

*Índice*
Configuração
Variáveis de Ambiente
Endpoints
Obter Usuário
Criar Usuário
Tratamento de Erros

*Configuração*
Para configurar esta aplicação, você precisa ter Node.js e npm instalados. Além disso, certifique-se de ter as credenciais AWS configuradas para acessar o DynamoDB.

Instalar dependências:
npm install

Implantar a aplicação usando AWS Lambda:
npm run deploy

*Variáveis de Ambiente*
USERS_TABLE: O nome da tabela DynamoDB onde os dados dos usuários são armazenados.

*Endpoints*
Obter Usuário
Endpoint: GET /users/:userId

Recupera os detalhes de um usuário com base no userId fornecido.

Requisição
Parâmetros de Caminho:
userId (string): O ID do usuário a ser recuperado.
Resposta
*Sucesso (200):

{
  "userId": "string",
  "name": "string",
  "email": "string"
}

*Usuário Não Encontrado (404):

{
  "error": "Não foi possível encontrar o usuário ID fornecido"
}

*Erro no Servidor (500):

{
  "error": "Não foi possível recuperar o usuário"
}

Criar Usuário
Endpoint: POST /users

Cria um novo usuário com os detalhes fornecidos.

*Requisição*
Parâmetros do Corpo:
userId (string): O ID do usuário a ser criado.
name (string): O nome do usuário.
email (string): O endereço de email do usuário.

Resposta
*Sucesso (200):

{
  "userId": "string",
  "name": "string",
  "email": "string"
}

*Erro no Servidor (500):

{
  "error": "Não foi possível criar o usuário"
}

*Tratamento de Erros
Se um endpoint não for encontrado, a API responde com um código de status 404 e o seguinte objeto JSON:

{
  "error": "Não encontrado"
}

Além disso, todos os erros do servidor respondem com um código de status 500 e uma mensagem de erro apropriada em português. As mensagens de erro incluem detalhes indicando se o erro ocorreu durante a recuperação do usuário ou a criação do usuário.