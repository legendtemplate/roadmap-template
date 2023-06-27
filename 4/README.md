```bash
import { NextPage } from "next";
import { productData } from "@/type/index";

interface IProps {
  product: productData;
}

const card: NextPage<IProps> = ({
  product: { image, title, slug, referenceList, discountprice, price },
}) => {
  return <span>{price}</span>;
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
