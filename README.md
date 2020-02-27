# VW-OAuth2Client

A  client library for OAuth2 authentication.
Allows to authorize HTTP requests using a token fetched from a token endpoint.

```
| settings authenticator accessToken tokenRequest request |
settings := OAuth2.Settings new.
settings tokenEndpoint: 'https://login.windows.net/someTenant/oauth2/token'.
authenticator := OAuth2.Authenticator fromSettings: settings.
" obtain a token (see subclasses of TokenRequest for alternative methods to get a token) "
tokenRequest :=  OAuth2.ClientCredentialsTokenRequest clientId: 'sampleClientId' secret: 'sampleSecret'.
accessToken := authenticator obtainAccessToken: tokenRequest.
" authorize the actual request "
request := Net.HttpRequest get: 'https://someTenant.sharepoint.com/sites/sampleSite/_api/lists'.
accessToken authenticateRequest: request
```
