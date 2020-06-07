# Errors

The Scale API uses conventional HTTP response codes to indicate the success or failure of an API request.

The following response and error codes are used:

| Code | Meaning |
| :--- | :--- |
| 200 - OK | Everything worked as expected. |
| 201 - OK | Resource created. |
| 400 - Bad Request | The request was invalid, often due to missing a required parameter. |
| 401 - Unauthorised | No valid API key provided. |
| 403 - Forbidden | Not authorised to access requested data. |
| 404 - Not Found | The requested resource could not be found. |
| 429 - Too many requests | Too many requests hit the API too quickly. |
| 500 - Server Error | Something went wrong on Scale's end. Rare but mainly resolved by trying again later.  |

 

