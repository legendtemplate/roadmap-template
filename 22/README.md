### Vercel Postgres
> [Framework start](https://vercel.com/docs/frameworks) <br /> 
> [Quick start](https://vercel.com/docs/storage/vercel-postgres/quickstart)

Make a database on dashboard on `storage tab` and make it.

***
### MongoDB
> First 
```bash
npm i express mongoose colors dotenv morgan cors
```
> .env
```bash
PORT = 8000
DEV_MODE = production
MONGODB_URL = '' 
```
> Server.js
```bash
import express from 'express';
import colors from 'colors';
import dotenv from 'dotenv';
import morgan from 'morgan';
import cors from "cors";
import connectDB from "./config/connection.js";

// env
dotenv.config();

// port
const port = process.env.PORT || 9000

const app = express();

//middelwares
app.use(cors());
app.use(express.json());
app.use(morgan("dev"));

// rest api
app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example apps listening ${process.env.DEV_MODE} on port ${port}`.bgBlue.white)
})
```
> config/connection.js
```bash
import mongoose from "mongoose";
import colors from "colors";

const connectDB = async () => {
  try {
    const conn = await mongoose.connect(
      "mongodb+srv://muzammilsafdar528982:qEzSQqcgRzOEStaJ@cluster0.gmu0trk.mongodb.net/?retryWrites=true&w=majority",
      {
        useNewUrlParser: true,
        useUnifiedTopology: true,
      }
    );
    console.log(
      `Conneted To Mongodb Databse ${conn.connection.host}`.bgMagenta.white
    );
  } catch (error) {
    console.log(`Errro in Mongodb ${error}`.bgRed.white);
  }
};

export default connectDB;

```




***
### Postgresql


***
### Firebase
npm install prisma --save-dev