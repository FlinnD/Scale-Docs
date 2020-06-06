# Idempotency

## Idempotent Requests

The API supports [idempotency](https://en.wikipedia.org/wiki/Idempotence) for safely retrying requests without accidentally performing the same operation twice. This is useful when an API call is disrupted in transit and you do not receive a response. For example, if a request to initiate a payment does not respond due to a network connection error, you can retry the request with the same idempotency key to guarantee that no more than one payment is created.

To perform an idempotent request, provide an additional `IdempotencyKey` element to the request headers in the following format:

```text
IdempotencyKey: <key> 
```

Idempotency keys are stored for 24 hours. Any requests made with the same key over 24 hours after the it is first seen by the Scale API will result in a new request being created.

When a repeated request is observed, we return the same response code and body as per the original request.

Idempotency keys are generated on the client and are recommended to use v4 UUIDs in order to avoid collisions.

Only `POST` requests accept idempotency keys. 

