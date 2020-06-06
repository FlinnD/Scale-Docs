# Authentication

## API Keys

The Scale API uses API keys to authenticate requests. You can view and manage your API keys in the Scale dashboard. 

## Usage

An API key consists of two parts: a `client-id` and a `client-secret`. This information should be handled with care.

To make an authenticated request to the Scale API, include the API Key in the `Authorization` header in HTTP request according the following format:

```text
Authorization: APIKey <client-id>:<client-secret>
```

## Permissions

Role-based access control \(RBAC\) is used to limit the permissions of API keys. These permissions are selected when the key is created and cannot be changed after creation. These permissions allow you to specify which sensitive actions may be performed by a key and should be configured according to your security posture. 

If a permission is not granted when using an API key, the API will return a HTTP 401 \(Unauthorized\) response.

## Expiration

API keys do not expire, but can be rotated or deleted within the dashboard \(required 2FA\).

