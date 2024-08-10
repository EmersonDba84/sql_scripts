# SQL Scripts

Este repositório contém scripts SQL para gerenciar a base de dados do projeto XYZ.

## Estrutura

- **schema/**: Contém scripts para criar as tabelas e definir a estrutura inicial do banco de dados.
- **seeds/**: Scripts para popular a base de dados com dados iniciais.
- **migrations/**: Scripts para realizar alterações incrementais na estrutura do banco de dados.

## Uso

1. Execute os scripts na pasta `schema/` para criar as tabelas.
2. Use os scripts na pasta `seeds/` para popular a base de dados.
3. Aplique as migrações conforme necessário usando os scripts em `migrations/`.


-- Criação da tabela "users" para armazenar informações de usuários
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,   -- Coluna "id" é a chave primária e será incrementada automaticamente
    username VARCHAR(50) NOT NULL,       -- Coluna "username" armazena o nome de usuário, com limite de 50 caracteres e não pode ser nulo
    email VARCHAR(100) NOT NULL,         -- Coluna "email" armazena o email do usuário, com limite de 100 caracteres e não pode ser nulo
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP -- Coluna "created_at" armazena a data e hora da criação do registro, com valor padrão sendo o timestamp atual
);

-- Criação da tabela "posts" para armazenar informações de postagens feitas pelos usuários
CREATE TABLE posts (
    id INT PRIMARY KEY AUTO_INCREMENT,   -- Coluna "id" é a chave primária e será incrementada automaticamente
    user_id INT,                         -- Coluna "user_id" armazena o id do usuário que fez a postagem, criando uma relação com a tabela "users"
    title VARCHAR(100),                  -- Coluna "title" armazena o título da postagem, com limite de 100 caracteres
    content TEXT,                        -- Coluna "content" armazena o conteúdo da postagem, sem limite de caracteres
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP, -- Coluna "created_at" armazena a data e hora da criação do registro, com valor padrão sendo o timestamp atual
    FOREIGN KEY (user_id) REFERENCES users(id)  -- Define a coluna "user_id" como chave estrangeira, referenciando a coluna "id" da tabela "users"
);


