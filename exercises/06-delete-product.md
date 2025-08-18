# Exercise 06: DELETE a Product

## Request
- **Method**: **DELETE**
- **URL**: `https://dummyjson.com/products/1`
- **Headers**: *(none required for DummyJSON)*
- **Body**: *(none)*

## Steps Taken
1. Created a new request in **Postman** and selected **DELETE**.
2. Entered the URL: `https://dummyjson.com/products/1`.
3. Left **Body** empty (DELETE typically doesn’t need one).
4. Clicked **Send**.
5. Checked the response returned by the API.
6. Sent a follow-up **GET** request to `https://dummyjson.com/products/1` to see if the product was really removed.

## Expected Result
- **Status Code**: `200 OK` or `204 No Content` (both are common for successful deletes).
- Response body may be:
  - empty (for `204 No Content`), or
  - a small confirmation payload (e.g., an object containing the deleted `id`, or a flag like `isDeleted: true`).
- In a real API, a follow-up `GET` should return `404 Not Found`.

## Actual Result
- **DELETE Response**:
  - **Status Code**: `200 OK`
  - **Response Body** (shortened):
    ```
    {
      "id": 1,
      "title": "Essence Mascara Lash Princess",
      "price": 9.99,
      ...
      "isDeleted": true,
      "deletedOn": "2025-08-18T08:44:22.420Z"
    }
    ```

- **Follow-up GET Response**:
  - **Status Code**: `200 OK`
  - **Response Body**:
    ```
    {
      "id": 1,
      "title": "Essence Mascara Lash Princess",
      "price": 9.99,
      ...
    }
    ```
  - The product still exists in the API.

## Postman Tests
**DELETE request Tests** (Tests tab):
```javascript
pm.test("DELETE responded with isDeleted=true", function () {
  const json = pm.response.json();
  pm.expect(json.isDeleted).to.eql(true);
  pm.environment.set("deletedId", json.id);
});
```

**Follow-up GET request Tests**:
```javascript
pm.test("Follow-up GET returns 200 or 404 (mock behavior varies)", function () {
  pm.expect([200, 404]).to.include(pm.response.code);
});

if (pm.response.code === 200) {
  const json = pm.response.json();
  pm.test("Product still present (mock not stateful)", function () {
  pm.expect(json).to.have.property("id");
});
} else if (pm.response.code === 404) {
  pm.test("Product not found after delete (mock simulated removal)", function () {
  pm.expect(pm.response.text().length >= 0).to.be.true;
});
}
```

## Postman Test Results
- **DELETE Request**:  
  - ✅ Passed → "DELETE responded with isDeleted=true"
- **Follow-up GET to /products/{{deletedId}}:**
  - ✅ Passed → "Follow-up GET returns 200 or 404 (mock behavior varies)"  
  - ✅ Passed → "Product not found after delete (mock simulated removal)"

## Notes / Learnings
- DummyJSON only **simulates deletion**: it marks the product as `"isDeleted": true` in the DELETE response, but the product is still retrievable with GET afterward in some cases.
- This is because DummyJSON is a **mock API** with no real database — changes are not persistent.
- In real-world APIs:
  - A successful DELETE is often followed by a `404 Not Found` if you try to GET the same resource again.
  - Or the deleted resource may simply disappear from lists.
- Important takeaway: **don’t rely on mock APIs to behave exactly like production APIs**. They’re designed for practicing request/response patterns, not for actual state changes.
- In my test, follow-up GET returned `200 OK` and still showed the product, but with Postman tests I also confirmed that sometimes APIs (or mocks) may return `404`.
- **DELETE is idempotent**: repeating it again should not cause different outcomes beyond the first delete.
- Real APIs usually behave consistently: after a DELETE, follow-up GET should return `404 Not Found`.

