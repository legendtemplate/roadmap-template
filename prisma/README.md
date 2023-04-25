This is a [Prisma](https://react.dev/) documentation.

# Prisma
Start a New Next Project.
```bash
npx create-next-app@latest folder-name
```

## Prisma schema:
file name is `schema.prisma` in folder structure. <br />
### Relational Database
1 ------ `A data source (PostgreSQL)` <br />
```bash
datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}
```

### MongoDB Database
1 ------ `A data source (MongoDB)` <br />

```bash
datasource db {
  provider = "mongodb"
  url      = env("DATABASE_URL")
}
```

2 ------ `generator (Prisma Client)`<br />

```bash
generator client {
  provider = "prisma-client-js"
  output   = "./generated/prisma-client-js"
}
```

3 ------ `Prisma model )`<br />
```bash
modal modal {

}
```
```bash
prisma generate --schema ./database/myschema.prisma
```
`@unique`
`@@unique`
`@id`
`@@id`
### Prisma Client:
### Prisma Migrate:
### Prisma Studio:

