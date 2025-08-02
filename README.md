# Order System

Este projeto implementa um sistema de pedidos com três interfaces: HTTP, GraphQL e gRPC.

## Como executar

1. **Suba os containers do Docker:**
   ```sh
   docker-compose up -d
   ```
   Isso irá criar o banco de dados MySQL e a tabela `order` automaticamente.

2. **Inicie o servidor Go:**
   ```sh
   go mod tidy
   cd cmd/ordersystem
   go run main.go wire_gen.go
   ```

## Endpoints disponíveis

- **HTTP:** Porta `8000`
- **GraphQL:** Porta `8080`
- **gRPC:** Porta `50051`

## Como testar

### HTTP

Utilize o arquivo `api/create_order.http` para testar as chamadas HTTP (pode usar o VS Code com extensão REST Client).

### gRPC

Use um cliente como [Evans](https://github.com/ktr0731/evans):

```sh
evans -r repl
```
Conecte em `localhost:50051` e utilize os métodos disponíveis.

### GraphQL

Acesse no navegador: [http://localhost:8080](http://localhost:8080)

#### Exemplo de mutation para criar um pedido:

```graphql
mutation {
  createOrder(input: {
    id:"1",
    Price: 100.0,
    Tax: 10.0
  }) {
    id
    Price
    Tax
    FinalPrice
  }
}
```

#### Exemplo de query para listar pedidos da página 1:

```graphql
query {
  listOrders(page: 1) {
    id
    Price
    Tax
    FinalPrice
  }
}
```

---

Pronto! Com esses passos você consegue executar e testar todas as interfaces do projeto.
