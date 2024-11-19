**# API REST de Jogos

Esta API RESTful foi desenvolvida em **Java 21** usando **Spring Boot**. Ela gerencia informações sobre jogos e listas de jogos, seguindo as boas práticas do padrão REST. A API suporta três ambientes (teste, desenvolvimento e produção) e utiliza bancos de dados H2 e PostgreSQL via Docker.

## Tecnologias Utilizadas

- **Java:** 21
- **Spring Boot:**
  - Spring Data JPA
  - Spring Web
- **Banco de Dados:**
  - H2 (para testes)
  - PostgreSQL (via Docker e local)
- **Gerenciamento de Dependências:** Maven
- **Ambientes Configurados:**
  - `test`: Banco H2
  - `dev`: Banco PostgreSQL local
  - `prod`: Banco PostgreSQL no Docker

---

## Estrutura do Projeto

- **Modelos (Entities):** Representam as tabelas do banco de dados.
- **DTOs:** Transferem os dados de forma controlada entre camadas.
- **Repositories:** Camada de persistência de dados.
- **Services:** Contém as regras de negócio.
- **Controllers:** Ponto de entrada para os endpoints da API.

---

## Endpoints da API

### **1. Jogos**
#### `GET /games`
Retorna uma lista com todos os jogos, exibindo informações resumidas definidas no `GameDTO`.

#### `GET /games/{id}`
Retorna detalhes completos de um jogo específico, identificado pelo seu ID.

---

### **2. Listas de Jogos**
#### `GET /lists`
Retorna os títulos de duas listas predefinidas:  
- **Aventura e RPG**
- **Jogos de Plataforma**

#### `GET /lists/{id}/games`
Retorna os jogos de uma lista específica, de acordo com o ID fornecido (1 ou 2).  

---

### **3. Alterar Posição de um Jogo na Lista**
#### `POST /{listId}/replacement`
Modifica a posição de um jogo em uma lista específica.

**Body do Request (JSON):**
```json
{
    "sourceIndex": 3,
    "destinationIndex": 1
}
**
