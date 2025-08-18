# Exercise 07: Error Handling (Non-existent Resource)

## Request A: GET Non-existent Product
- **Method**: **GET**
- **URL**: `https://dummyjson.com/products/99999`  
  (using a very large ID that should not exist)

## Steps Taken
1. Sent a GET request for product id `99999` in Postman.
2. Observed the status code and body.

## Expected Result
- **Status Code**: `404 Not Found`
- Response body should include an error message (e.g., "Product not found").

## Actual Result
- **Status Code**: `404 Not Found`
- **Response Body**:
```json
{
    "message": "Product with id '99999' not found"
}
```
## Postman Tests
```javascript
pm.test("GET non-existent returns 404", function () {
  pm.expect(pm.response.code).to.eql(404);
});
```
- **Test Result:** ✅ Passed → GET non-existent returns 404

---

## Request B: DELETE Non-existent Product
- **Method**: DELETE
- **URL**: https://dummyjson.com/products/99999

## Steps Taken
1. Sent a DELETE request for product id 99999.
2. Observed the status code and body.

## Expected Result
- **Status Code**: `404 Not Found`  
  (some mock APIs may return `200 OK` to keep delete idempotent)
- Body may contain an error message or a minimal confirmation payload.

## Actual Result
- **Status Code**: `404 Not Found`
- **Response Body**:
```json
{
    "message": "Product with id '99999' not found"
}
```

## Postman Tests
```javascript
pm.test("DELETE non-existent returns 200 or 404 (mock behavior)", function () {
  pm.expect([200, 404]).to.include(pm.response.code);
});
```
- **Test Result:** ✅ Passed → DELETE non-existent returns 200 or 404 (mock behavior)

## Notes / Learnings
- Error handling is essential when working with APIs; always verify both **status codes** and the **body**.
- Real production APIs typically return `404 Not Found` for resources that don’t exist.
- Mock APIs like DummyJSON may choose different behaviors for simplicity; write tests that reflect the **documented behavior** of the API you’re using.
- For DELETE operations, many systems favor **idempotence**; repeating a delete on a missing resource should not cause failures, which is why some return `200 OK` even when nothing was actually deleted.
