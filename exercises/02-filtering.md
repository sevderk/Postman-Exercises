# Exercise 02: Filtering Data

## Request
- **Method**: GET
- **URL**: https://dummyjson.com/products?limit=5&select=title,price

## Steps Taken
1. Sent a **GET** request to `https://dummyjson.com/products` in Postman.
2. Added query parameters in the **Params tab**:
   - `limit=5` → fetch only 5 products
   - `select=title,price` → include `title` and `price` fields (note: `id` is still returned by default).
3. Clicked **Send** and checked the response body in JSON format.
4. Used Postman’s **Filter (JSONPath)** to explore:
   - `$.products[*].title` → showed all product titles in the array.
   - `$.products[0].price` → showed the price of the first product (9.99).

## Expected Result
- JSON array with 5 product objects.
- Each object should include:
  - `id` (always returned by DummyJSON, even if not selected)
  - `title`
  - `price`

## Actual Result
- **Status Code**: 200 OK
- Response:

```json
{
    "products": [
        {
            "id": 1,
            "title": "Essence Mascara Lash Princess",
            "price": 9.99
        },
        {
            "id": 2,
            "title": "Eyeshadow Palette with Mirror",
            "price": 19.99
        },
        {
            "id": 3,
            "title": "Powder Canister",
            "price": 14.99
        },
        {
            "id": 4,
            "title": "Red Lipstick",
            "price": 12.99
        },
        {
            "id": 5,
            "title": "Red Nail Polish",
            "price": 8.99
        }
    ],
    "total": 194,
    "skip": 0,
    "limit": 5
}
```

## Postman Filter Results:
- $.products[*].title

```json
[
    "Essence Mascara Lash Princess",
    "Eyeshadow Palette with Mirror",
    "Powder Canister",
    "Red Lipstick",
    "Red Nail Polish",
    "Calvin Klein CK One",
    "Chanel Coco Noir Eau De",
    "Dior J'adore",
    "Dolce Shine Eau de",
    "Gucci Bloom Eau de",
    "Annibale Colombo Bed",
    "Annibale Colombo Sofa",
    "Bedside Table African Cherry",
    "Knoll Saarinen Executive Conference Chair",
    "Wooden Bathroom Sink With Mirror",
    "Apple",
    "Beef Steak",
    "Cat Food",
    "Chicken Meat",
    "Cooking Oil",
    "Cucumber",
    "Dog Food",
    "Eggs",
    "Fish Steak",
    "Green Bell Pepper",
    "Green Chili Pepper",
    "Honey Jar",
    "Ice Cream",
    "Juice",
    "Kiwi"
]
```
- $.products[0].price

```json
[
    9.99
]
```

## Notes / Learnings
- API-level filtering = query parameters (`limit`, `select`, etc.).
- Postman filtering = JSONPath in the UI to quickly inspect results.
- DummyJSON always returns the `id` field, even if you don’t include it in `select`.
- Selected fields (`title`, `price`) are shown alongside `id`.
- Important: `id` is kept so each product remains uniquely identifiable.
