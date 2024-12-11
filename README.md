```markdown
# Product API

## Descrição

A Product API é uma aplicação Spring Boot que fornece uma API RESTful para gerenciar produtos. 
A API permite criar, listar, atualizar e deletar produtos, além de fornecer links HATEOAS para navegação entre os recursos.

## Tecnologias Utilizadas

- Java 17
- Spring Boot 3.4.0
- Spring Data JPA
- Spring Boot Starter Validation
- Spring Boot Starter Web
- Spring Boot Starter HATEOAS
- PostgreSQL
- Maven

## Pré-requisitos

- Java 17 ou superior
- Maven 3.6.0 ou superior
- PostgreSQL

## Configuração do Banco de Dados

1. Instale e configure o PostgreSQL.
2. Crie um banco de dados chamado `productdb`.
3. Configure as credenciais de acesso ao banco de dados no arquivo `application.properties`:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/productdb
spring.datasource.username=seu_usuario
spring.datasource.password=sua_senha
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

## Executando a Aplicação

1. Clone o repositório:

```sh
git clone https://github.com/linconvinicius/products-api.git
cd product-api
```

2. Compile e execute a aplicação usando Maven:

```sh
mvn spring-boot:run
```

A aplicação estará disponível em `http://localhost:8080`.

## Endpoints da API

### Criar Produto

- **URL:** `/products`
- **Método:** `POST`
- **Corpo da Requisição:**

```json
{
  "name": "Nome do Produto",
  "value": 100.00
}
```

- **Resposta de Sucesso:**

```json
{
  "idProduct": "UUID",
  "name": "Nome do Produto",
  "value": 100.00,
  "_links": {
    "self": {
      "href": "http://localhost:8080/products/UUID"
    }
  }
}
```

### Listar Todos os Produtos

- **URL:** `/products`
- **Método:** `GET`
- **Resposta de Sucesso:**

```json
[
  {
    "idProduct": "UUID",
    "name": "Nome do Produto",
    "value": 100.00,
    "_links": {
      "self": {
        "href": "http://localhost:8080/products/UUID"
      }
    }
  }
]
```

### Obter Produto por ID

- **URL:** `/products/{id}`
- **Método:** `GET`
- **Resposta de Sucesso:**

```json
{
  "idProduct": "UUID",
  "name": "Nome do Produto",
  "value": 100.00,
  "_links": {
    "self": {
      "href": "http://localhost:8080/products/UUID"
    },
    "Lista de produtos": {
      "href": "http://localhost:8080/products"
    }
  }
}
```

### Atualizar Produto

- **URL:** `/products/{id}`
- **Método:** `PUT`
- **Corpo da Requisição:**

```json
{
  "name": "Nome do Produto Atualizado",
  "value": 150.00
}
```

- **Resposta de Sucesso:**

```json
{
  "idProduct": "UUID",
  "name": "Nome do Produto Atualizado",
  "value": 150.00,
  "_links": {
    "self": {
      "href": "http://localhost:8080/products/UUID"
    }
  }
}
```

### Deletar Produto

- **URL:** `/products/{id}`
- **Método:** `DELETE`
- **Resposta de Sucesso:**

```json
{
  "message": "Produto removido com sucesso!"
}
```

## Testes

Para executar os testes, utilize o comando:

```sh
mvn test
```

## Caso queira contribuir

1. Faça um fork do projeto.
2. Crie uma branch para sua feature (`git checkout -b feature/nova-feature`).
3. Commit suas mudanças (`git commit -am 'Adiciona nova feature'`).
4. Faça o push para a branch (`git push origin feature/nova-feature`).
5. Crie um novo Pull Request.
