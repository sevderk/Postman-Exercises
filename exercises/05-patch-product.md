# Exercise 05: PATCH (Partially Update a Product)

## Request
- **Method**: **PATCH**
- **URL**: `https://dummyjson.com/products/1`
- **Headers**:
  - `Content-Type: application/json`
- **Body** (raw, JSON):
```json
{
"price": 15.99
}
```
6. Clicked **Send**.

## Expected Result
- **Status Code**: `200 OK`
- JSON response with:
- Same `id` (1).
- `price` updated to `15.99`.
- Other fields unchanged.

## Actual Result
- **Status Code**: `200 OK`
- **Response Body**:
```json
{
    "id": 1,
    "title": "Essence Mascara Lash Princess",
    "price": 15.99,
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
- **PATCH** updates only the fields you provide; the rest stay unchanged.
- **PUT** is technically meant for full replacements, but in DummyJSON it behaves like PATCH and leaves other fields unchanged as well.
- Always read API documentation to know whether to use **PUT** or **PATCH**.
- In real-world APIs, sending only part of the object with **PUT** might wipe out the missing fields — so be careful!
