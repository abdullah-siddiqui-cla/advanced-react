### Note
Please don't focus much on the styling part in these hands-on exercises, as the primary focus is to get comfortable with advanced React topics. The styling provided in the previews is minimal and intended solely for demonstrating the expected end result.

# 1. Basic Input Focus
## Objective:
Create an input field and a button. On button click, the input field should gain focus.

## Steps:
- Use `useRef` to create a ref for the input field.
- Attach the `ref` to the input element.
- On button click, invoke the focus() method on the input element.

## Preview
See `task-1-preview.mov` file

# 2. Search Input with Forwarding Refs
## Objective:
Create a `SearchInput` component (code given below) that forwards its `ref` to the inner `input`. Add a button to focus the input programmatically.

## Steps:
- Create a `SearchInput` component using `React.forwardRef`.
- Attach the forwarded ref to the `<input>` element inside `SearchInput`.
- Use the component in a parent and pass a `ref` to it.
- Add a button in the parent to focus the input using the `ref`.
- Hint: Code for `SearchInput` component. You have to implement the `ref` part in the task.
```
const SearchInput = () => {
  return (
    <div className="relative">
      <input
        className="outline-none focus:outline-none rounded p-2 focus:border-purple-400 focus:border border border-black peer"
        type="text"
      />
      <div className="w-full absolute top-full peer-focus:flex hidden">
        <div className="p-2 flex justify-center w-full bg-gray-100 border border-gray-200 shadow">
          <p className="text-gray-500 text-base">Search...</p>
        </div>
      </div>
    </div>
  );
};
```

## Preview
See `task-2-preview.mov` file

# 3. Cart Context
## Objective:
Create a `CartContext` for managing cart items. Add static products to a page and let users add/remove items from the cart. Display an "already added" flag on products in the cart.

## Steps:
- Create a `CartContext` with `React.createContext`.
- `Provide` the cart state and functions (`addToCart`, `removeFromCart`) via the context.
- Build a product list with static data and allow users to add/remove products.
- Display an "already added" flag for products in the cart.
- Hint: Here's the code for the components that render the products. You just have to create a context for cart and use it inside the `ProductCard` component to manage the "Add to Cart" behavior.  

```
const ProductCard = ({ product }) => {
  const isAdded = false;

  return (
    <div className="col-span-1 p-2 bg-gray-200 shadow flex flex-col gap-y-2 *:w-full">
      <h4 className="text-2xl">{product.name}</h4>

      <div className="flex justify-end">
        <button
          className="p-2 rounded flex items-center disabled:bg-gray-100 disabled:cursor-not-allowed disabled:text-gray-600 border border-purple-500 bg-white hover:bg-gray-200 text-black"
          disabled={isAdded}
        >
          {isAdded ? "Already Added" : "Add to Cart"}
        </button>
      </div>
    </div>
  );
};

const Products = () => {
  const products = [
    { id: 1, name: "Product 1" },
    { id: 2, name: "Product 2" },
    { id: 3, name: "Product 3" },
    { id: 4, name: "Product 4" },
    { id: 5, name: "Product 5" },
    { id: 6, name: "Product 6" },
    { id: 7, name: "Product 7" },
    { id: 8, name: "Product 8" },
    { id: 9, name: "Product 9" },
    { id: 10, name: "Product 10" },
  ];

  return (
    <>
      <h1 className="text-6xl mb-3 py-4 max-w-6xl mx-auto">Task 3</h1>
      <div className="flex flex-col max-w-6xl mx-auto gap-y-3">
        <h1 className="text-3xl">Products</h1>
        <div className="w-full grid grid-cols-3 gap-2">
          {products.map((product) => (
            <ProductCard key={product.id} product={product} />
          ))}
        </div>
      </div>
    </>
  );
};

```

## Preview
See `task-3-preview.mov` file

# 4. Replacing Static Products with Axios
## Objective:
Fetch products from an API using `axios` and replace the static data. Dynamically render the product list.

## Steps:
- Use `Axios` to fetch products from an API (e.g., `https://dummyjson.com/products`).
- Replace the static products array with fetched data.
- Display products dynamically.
- Hint: Update the `Products` component above to keep `products` in a state. When the component is mounted, use `axios` to fetch products and set them to `products` state.
  - For on mount hooks, you can use `useEffect` as follows,
  ```
    useEffect(() => {
      ...
    }, [])
  ```

## Preview
See `task-4-preview.mov` file
