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
npm i express colors mongoose dotenv morgan cors
```
##### .env file
```bash
MONGO_URL = ''
DEV_MODE = 'production'
PORT = 7000
```

##### [Express](http://expressjs.com/)

```bash
import express from 'express'

const app = express();
const PORT = 8000 || process.env.PORT;
app.use(express.json());


app.listen(PORT, () => {
    console.log(`Server ${process.env.DEV_MODE} running on port ${PORT}`.bgCyan.white);
});
```

##### [Colors](https://www.npmjs.com/package/colors)

```bash
import colors from 'colors'
```

##### dotenv 

```bash
import morgan from 'morgan'
dotenv.config();
```

##### morgan 

```bash
import dotenv from 'dotenv'
app.use(morgan("dev"));
```

##### cors 

```bash
import cors from 'cors'
app.use(cors());
```

##### Mongoose

```bash
// import main file
import connectDB from "./config/db.js";
connectDB();
// file in config/db.js
import mongoose from "mongoose";
import colors from "colors";

const connectDB = async () => {
  try {
    const uri = process.env.MONGO_URL
    const conn = await mongoose.connect(uri ,{
        useNewUrlParser:true,
        useUnifiedTopology:true
    });
    console.log(
      `Conneted To Mongodb Databse ${conn.connection.host}`.bgMagenta.white
    );
  } catch (error) {
    console.log(`Errro in Mongodb ${error}`.bgRed.white);
  }
};

export default connectDB;

```

##### Model 

```bash
import mongoose from "mongoose";

const productSchema = new mongoose.Schema(
  {
    name: {
      type: String,
      required: true,
    },
  },
  {
    timestamps: true,
  }
);

export default mongoose.model("Product", productSchema);

```


##### Controller 
```bash
import productModel from "../model/productModel.js";
```

```bash
// create
export const createCategoryController = async (req, res) => {
  try {
    const { name, description, number } = req.body;

    const category = await new productModel({
      name,
      number,
      description,
    }).save();
    res.status(200).send({
      success: true,
      message: "new category created",
      category,
    });
  } catch (error) {
    console.log(error);
    res.status(500).send({
      success: false,
      message: "Errro in Category",
      error,
    });
  }
};

```

```bash
// update
export const updateCategoryController = async (req, res) => {
  try {
    const { name, description, number } = req.body;
    const { id } = req.params;
    const category= await productModel.findByIdAndUpdate(id, { name,description, number  }, { new: true });

    res.status(200).send({
      success: true,
      messsage: "Category Updated Successfully",
      category,
    });
  } catch (error) {
    console.log(error);
    res.status(500).send({
      success: false,
      error,
      message: "Error while updating category",
    });
  }
};
```

```bash
// delete
export const deleteCategoryController = async (req, res) => {
  try {
    const { id } = req.params;
    const category = await productModel.findByIdAndDelete(id);
    res.status(200).send({
      success: true,
      message: "Categry Deleted Successfully",
      category
    });
  } catch (error) {
    console.log(error);
    res.status(500).send({
      success: false,
      message: "error while deleting category",
      error,
    });
  }
};
```

```bash
// get all cat
export const categoryControlller = async (req, res) => {
  try {
    const category = await productModel.find();
    res.status(200).send({
      success: true,
      message: "All Categories List",
      category,
    });
  } catch (error) {
    console.log(error);
    res.status(500).send({
      success: false,
      error,
      message: "Error while getting all categories",
    });
  }
};
```


##### Routes
```bash
import express from "express";
import {
  createCategoryController,
  updateCategoryController,
  deleteCategoryController,
  categoryControlller,
  singleCategoryController,
} from "../controller/categoryController.js";

const router = express.Router();

router.post("/create-category", createCategoryController);
router.put("/update-category/:id", updateCategoryController);
router.delete("/delete-category/:id", deleteCategoryController);
router.get("/get-category", categoryControlller);
router.get("/get-category/:id", singleCategoryController);

export default router;
```

```bash
// export router
import productRoutes from "./routes/productRoutes.js";
app.use('/products', productRoutes);

```
