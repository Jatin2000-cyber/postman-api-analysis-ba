# Postman exports

Place the two exported files here:

- `ecommerce-api-analysis.postman_collection.json` (the collection with TC-01 to TC-12)
- `dummyjson-test.postman_environment.json` (the environment with base_url, username, password, token)

## How to use
1. In Postman, click **Import** and select both files.
2. Select the `DummyJSON - Test` environment in the top-right dropdown.
3. Run **TC-01 - Login valid** first. Its post-response script saves the access token into `{{token}}`.
4. Run the remaining requests in any order.

The username and password are DummyJSON's public test credentials. No private data is stored in these files.
