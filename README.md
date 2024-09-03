
# UsuariosAPI

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

## Descrição

**UsuariosAPI** é uma API criada em C# utilizando a biblioteca Identity. Esta API permite a criação de usuários e o acesso ao sistema através de login e senha, utilizando autenticação via token JWT (JSON Web Token). 

## Funcionalidades

- **Criação de Usuários:** Permite a criação de novas contas de usuários no sistema.
- **Login:** Autenticação de usuários através de login e senha.
- **Autenticação JWT:** Geração de tokens JWT para autenticação e autorização em endpoints protegidos.
- **Proteção de Endpoints:** Alguns endpoints da API estão protegidos e só podem ser acessados por usuários autenticados.

## Tecnologias Utilizadas

- **C#:** Linguagem de programação utilizada para o desenvolvimento da API.
- **ASP.NET Core:** Framework utilizado para a construção da API.
- **ASP.NET Core Identity:** Biblioteca utilizada para gerenciamento de usuários e autenticação.
- **JWT (JSON Web Token):** Método de autenticação baseado em tokens.

## Pré-requisitos

Antes de começar, certifique-se de que você tem os seguintes requisitos instalados:

- [.NET Core SDK](https://dotnet.microsoft.com/download)
- [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) ou outro banco de dados compatível.

## Configuração do Projeto

1. Clone o repositório:

    ```bash
    git clone https://github.com/maulru/UsuariosAPI.git
    ```

2. Navegue até o diretório do projeto:

    ```bash
    cd UsuariosAPI
    ```

3. Restaure as dependências do projeto:

    ```bash
    dotnet restore
    ```

4. Configure a string de conexão do banco de dados no arquivo `appsettings.json`:

    ```json
    {
      "ConnectionStrings": {
        "DefaultConnection": "Server=.;Database=UsuariosAPIDb;Trusted_Connection=True;MultipleActiveResultSets=true"
      }
    }
    ```

5. Aplique as migrações do banco de dados:

    ```bash
    dotnet ef database update
    ```

6. Execute o projeto:

    ```bash
    dotnet run
    ```

## Endpoints

### Criação de Usuário

- **URL:** `/api/account/register`
- **Método:** `POST`
- **Corpo da Requisição:**

    ```json
    {
      "username": "string",
      "password": "string",
      "email": "string"
    }
    ```

- **Resposta:**

    - `201 Created` em caso de sucesso.
    - `400 Bad Request` em caso de erro.

### Login

- **URL:** `/api/account/login`
- **Método:** `POST`
- **Corpo da Requisição:**

    ```json
    {
      "username": "string",
      "password": "string"
    }
    ```

- **Resposta:**

    - `200 OK` com o token JWT em caso de sucesso.
    - `401 Unauthorized` em caso de falha na autenticação.

## Uso de Tokens JWT

Após o login, o token JWT retornado deve ser incluído no cabeçalho de todas as requisições para endpoints protegidos:

```http
Authorization: Bearer <seu-token-jwt>
```

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).
