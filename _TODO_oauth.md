# OAuth

* Heavily inspired by [PortSwigger - Web Security Academy](https://portswigger.net/web-security/oauth)  

## Check if OAuth is in place

* If there is a third party login option, it is probably OAuth  
* Check for requests to an `/authorization` endpoint with params like `client_id`, `redirect_uri` and `respone_type`.  

## Recon

Check configuration by `GET`ting following standard endpoints:  
```
/.well-known/oauth-authorization-server
/.well-known/openid-configuration
```

## Grant types

### Authorization code

1. Authorization request
2. User login (via OAuth provider)
3. Authorization code grant
4. Access token request
5. Access token grant
6. API call
7. Resource grant

Details: [PortSwigger - Web Security Academy](https://portswigger.net/web-security/oauth/grant-types#authorization-code-grant-type)

### Implicit grant type

1. Authorization request
2. User login (via OAuth provider)
3. Access token grant
4. API call
5. Resource grant

Details: [PortSwigger - Web Security Academy](https://portswigger.net/web-security/oauth/grant-types#implicit-grant-type)

## OpenID Connect


