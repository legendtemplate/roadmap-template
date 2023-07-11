### Prisma 
> [Quickstart](https://vercel.com/guides/nextjs-prisma-postgres) <br /> 

***

First
```bash
npm install prisma @prisma/client
```
then init
```bash
npx prisma init
```

push to database for making tables
```bash
npx prisma db push
```

show table on studio
```bash
npx prisma studio
```

generate
```bash
npx prisma generate
```

***



### Node JS

```bash
npm i express colors
```
##### [Express](http://expressjs.com/)

```bash
import express from 'express'

const app = express();
const PORT = 8000 
app.use(express.json());


app.listen(PORT, () => {
    console.log(`Server running on port ${PORT}`)
})
```

##### [Colors](https://www.npmjs.com/package/colors)

```bash
import colors from 'colors'
```

##### dotenv 
