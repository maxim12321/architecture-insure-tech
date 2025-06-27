# Проектирование GraphQL API

Получившийся GraphQL API будет выглядеть следующим образом:

```graphql
type Query {
    client(id: String!): Client
    documents(clientId: String!): [Document!]
    relatives(clientId: String!): [Relative!]
}

type Client {
    id: String!
    name: String
    age: Int
    documents: [Document!]
    relatives: [Relative!]
}

type Document {
    id: String!
    type: String
    number: String
    issueDate: String
    expiryDate: String
}

type Relative {
    id: String!
    relationType: String
    name: String
    age: Int
}
```

Тогда, например, запрос информации по клиенту будет выглядеть так:
```graphql
{
    client(id: "123") {
        id
        name
        age
    }
}
```

Для документов и родственников тоже определен отдельный `query`, а выбирать
отдельные поля можно будет по аналогии с `client()`. Примеры с полным набором
полей:

```graphql
{
    documents(clientId: "123") {
        id
        type
        number
        issueDate
        expiryDate
    }
}
```

```graphql
{
    relatives(clientId: "123") {
        id
        relationType
        name
        age
    }
}
```
