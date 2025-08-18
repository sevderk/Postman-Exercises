# Exercise 03: POST a New Product

## Request
- **Method**: POST
- **URL**: https://dummyjson.com/products/add
- **Headers**:
  - `Content-Type: application/json`
- **Body** (raw, JSON):
```json
{
  "title": "Hand Cream",
  "price": 7
}
```
## Steps Taken
1. Created a new request in **Postman** and selected **POST**.
2. Entered the URL: `https://dummyjson.com/products/add`
3. Added a header: `Content-Type: application/json`
4. Went to the **Body** tab → chose **raw** → selected **JSON**.
5. Pasted the product JSON:
```json
{ "title": "Hand Cream", "price": 7 }
```
6. Clicked **Send**.

## Expected Result
- **Status Code**: `201 Created`
- JSON response with the new product, including:
- A generated **id**.
- The fields I sent (**title**, **price**).

## Actual Result
- **Status Code**: `201 Created`  
- **Response Body**:
```json
{
    "id": 195,
    "title": "Hand Cream",
    "price": 7
}
```

## Notes / Learnings
- Unlike **GET**, **POST** requests must include a body with the data you’re creating.
- The `Content-Type: application/json` header tells the server we’re sending JSON.
- The API auto-generated a new **id** for the created product.
- **201 Created** is the proper REST status code when a new resource is successfully added.
