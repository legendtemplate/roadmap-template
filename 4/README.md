```bash
import { NextPage } from "next";
import Image from "next/image";
import Link from "next/link";
import { Product } from "@/types/product/page";

interface IProps {
  product: Product;
}

const card: NextPage<IProps> = ({
  product: {
    image,
    title,
    slug,
    catgeory,
    subcatgeory,
    brand,
    discountprice,
    price,
  },
}) => {
  return ();
};
export default card;
```


### Next JS

***

### Remix JS

***

### Gatsby JS

***

### Expo (for apps)
