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

```javascript
const { auth } = require("express-openid-connect");

const config = {
  authRequired: false,
  auth0Logout: true,
  secret: "a long, randomly-generated string stored in env",
  baseURL: "http://localhost:3000",
  clientID: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  issuerBaseURL: "https://xxxxxxxx.xxx.xx.auth0.com",
};

// auth router attaches /login, /logout, and /callback routes to the baseURL
app.use(auth(config));

// req.isAuthenticated is provided from the auth router
app.get("/", (req, res) => {
  res.send(req.oidc.isAuthenticated() ? "Logged in" : "Logged out");
});
```
