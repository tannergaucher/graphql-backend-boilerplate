# GraphQL Backend Boilerplate

## Graphql Yoga server + Prisma DB + JWT Authentication

TODO BEFORE PUSH: remove endpoint from prisma.yml

---

## Installation

- Remove `.sample` suffix from the environment variables file to make it `.env`

- `npm install`

- Make sure prisma-cli is installed globally `npm install -g prisma`

- Authenticate with prisma via the cli: `prisma login`

- Deploy datamodel to Prisma: `prisma deploy`

- Key down to select demo server option:

- **_'Or deploy to an existing Prisma server:"_**

  Then choose:

  **_Demo server + MySQL database in Prisma Cloud_**

- Chose region of hosted demo server
  and hit `enter` for default server names

- Finally, start server: `npm start` and visit http://localhost:4000 to see your graphQL playground

## Testing backend with GraphQL Playground

### Sign up a user:

```graphql
mutation {
  signup(email: "FOO@FOO.com", password: "FOO", name: "Foo") {
    token
    user {
      id
      name
      email
      password
    }
  }
}
```

### Test an authenticated query using http headers in graphql playgrounnd:

Copy the token returned from the above `signup` mutation and place in the HTTP Headers section of the playground like so:

```json
{
  "Authorization": "Bearer <TOKEN>"
}
```

Note the space between Bearer and token

### Open up a new tab in the playground and test the authorized `me` query

```graphql
{
  me {
    id
    name
    password
    email
  }
}
```

This query gets the user id from the JWT pasted into the headers and returns the user's information
