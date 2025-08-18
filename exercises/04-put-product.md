# Exercise 04: PUT (Update a Product)

## Request
- **Method**: **PUT**
- **URL**: `https://dummyjson.com/products/1`
- **Headers**:
  - `Content-Type: application/json`
- **Body** (raw, JSON):
```json
{
"title": "Updated Essence Mascara Lash Princess",
"price": 12.99
}
```

## Steps Taken
1. Created a new request in **Postman** and selected **PUT**.
2. Entered the URL: `https://dummyjson.com/products/1` (updating product with id = 1).
3. Added a header: `Content-Type: application/json`.
4. Went to the **Body** tab → chose **raw** → selected **JSON**.
5. Entered the updated fields:
```json
{ "title": "Updated Essence Mascara Lash Princess", "price": 12.99 }
```
6. Clicked **Send**.

## Expected Result
- **Status Code**: `200 OK`
- JSON response with:
- The updated `title` and `price`.
- The same product `id` (1).

## Actual Result
- **Status Code**: `200 OK`
- **Response Body**:
```json
{
    "id": 1,
    "title": "Updated Essence Mascara Lash Princess",
    "price": 12.99,
    "discountPercentage": 10.48,
    "stock": 99,
    "rating": 2.56,
    "images": [
        "https://cdn.dummyjson.com/product-images/beauty/essence-mascara-lash-princess/1.webp"
    ],
    "thumbnail": "https://cdn.dummyjson.com/product-images/beauty/essence-mascara-lash-princess/thumbnail.webp",
    "description": "The Essence Mascara Lash Princess is a popular mascara known for its volumizing and lengthening effects. Achieve dramatic lashes with this long-lasting and cruelty-free formula.",
    "brand": "Essence",
    "category": "beauty"
}
```

## Notes / Learnings
- **PUT** is used to replace or fully update an existing resource.
- DummyJSON accepts partial updates with PUT, but some APIs require the *entire object* to be re-sent.
- **PATCH** is another method often used for partial updates (e.g., changing only `price`).
- Always check the API docs to see whether `PUT` or `PATCH` is preferred.
