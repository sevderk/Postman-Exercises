# Exercise 01: GET Products

## Request
- **Method**: GET
- **URL**: https://dummyjson.com/products

## Steps Taken
1. Opened Postman → New Request.
2. Chose `GET`.
3. Entered the URL and clicked **Send**.

## Expected Result
- JSON array with product info.

## Actual Result
- Response code: `200 OK`
- Response body (shortened):

```json
{
  "products": [
    {
      "id": 1,
      "title": "Essence Mascara Lash Princess",
      "description": "The Essence Mascara Lash Princess is a popular mascara known for its volumizing and lengthening effects. Achieve dramatic lashes with this long-lasting and cruelty-free formula.",
      "category": "beauty",
      "price": 9.99,
      ...
    },
    ...
  ]
}
```

## Notes / Learnings
- GET requests don’t need a body (only URL + query params).
- JSON response is structured as products: [].
- Next: try filtering with ?limit=5.
