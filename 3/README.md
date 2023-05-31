### [React JS](https://docs.google.com/document/d/1WeSRe-6-mFL3aRbShDjB0O8X_TQ8AiR_jOOZYmSWf3o/edit)

> Map function Fetch Data
```bash

  const [filteredCards, setFilteredCards] = useState(Cards); // Card mean map function

{filteredCards.map((data) => {
          const { href, img, label, id } = data;
          return (
            <Link href={data.href} key={id}></Link>
          );
        })}
```

***

> Map function Fetch Data load
```bash

const imagePerRow = 3;

  const [filteredCards, setFilteredCards] = useState(Cards); // Card mean map function
const [next, setNext] = useState(6);

  const loadMorePets = () => {
    setNext(next + imagePerRow);
  };

{filteredCards.slice(0, next).map((data) => {
          const { href, img, label, id } = data;
          return (
            <Link href={data.href} key={id}></Link>
          );
        })}
           <Button
          className="py-2 px-6 bg-red-500 text-white rounded-md"
          onClick={loadMorePets}
        >
          Load More
        </Button>
```

***

> Map function Fetch Data load and filter
```bash

```

***

### React Native JS