
# Next Js 13

All the basic information about the Next.js

## Next Js File Structure:

It should be in the src/app

for Eg: About Page 

1) make a folder with the name about
2) make a page.js file inside that folder 

    Something Look like :

        src/app/about/page.js

## Nested File Structure

- src
  - app
    - product
      - product1
        - page.js
      - product2
        - page.js
      - page.js


## Dynamic Routing

- src
  - app
    - product
      - [productId]
         - page.js
      - page.js


### Client-side Rendering or using the Hooks

If you want to use hooks or use client-side Rendering use 

```
 "use client" 
```


at the Top of the code


### Here the Routing is Dynamic
Means inside the [productId] folder's page.js file we have to use param

For that first import
```
 import { useRouter } from "next/navigation";

 ```

```
function page(param) {
  const router = useRouter();
  const [Product, setProduct] = useState(null);
  useEffect(() => {
    fetch(`https://fakestoreapi.com/products/${param.params.productId}`)
      .then((res) => res.json())
      .then((json) => {
        setProduct(json);
        console.log(param);
        console.log(json);
      });
  }, []);

  return <div>{Product && Product.title}</div>;
}

export default page;
```

Here the param is important which is returing the object of 

```
{params: {…}, searchParams: {…}}
params: {
    productId: '10'
}
searchParams: {

}

```







