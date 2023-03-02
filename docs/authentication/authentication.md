# Authentication

Welcome to Superkul API integration, first things before you integrate with us make sure you have access to our API. To get access token please login to dashboard and go to menu API Token

## Scenario Auth Token
After get token from customer dashboard you can pass the authentication token to `Header` `x-auth-token` every request what you want

example:
```http request
curl --location 'https://sandbox-api.superkul.id/v1/login/google' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--header 'x-auth-token' \
```


## Information Host

### Sandbox
- `web admin` https://sandbox.superkul.id
- `api` https://sandbox-api.superkul.id
- `mapi` https://test-api.superkul.id/api

### Production
- `web admin`  https://webadmin.superkul.id/
- `external` https://external.superkul.id/api

