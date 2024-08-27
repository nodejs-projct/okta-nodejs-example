## Install dependencies
Your application will need the `express-openid-connect` package which is an Auth0-maintained OIDC-compliant library for Express.

```sh
npm install express express-openid-connect --save
```

### Configure Router

The Express OpenID Connect library provides the `auth` router in order to attach authentication routes to your application. You will need to configure the router with the following configuration keys:

- `baseURL` - The URL where the application is served
- `secret` - A long, random string
- `issuerBaseURL` - The Domain as a secure URL found in your Application settings
- `clientID` - The Client ID found in your Application settings
