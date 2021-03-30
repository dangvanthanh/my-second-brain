Tags: #nodejs 

---

# HTTPs All The Things

  

In an express application, there are serveral things you need to do to sure you're serving your site over `https`. First, make sure the \`Strict-Transport-Security\` header (often abbreviated as [HSTS](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Strict-Transport-Security)) is set on the response. This instructs the browser to always send request over `https`.
  

Then make sure that you're any `http` request that make it to the server to the same url over `https`. The [express-enforce-ssl](https://www.npmjs.com/package/express-enforces-ssl) middleware provides an easy way to do this.

  

```javascript

const express = require('express');

const expressEnforceSSL = require('express-enforce-ssl');

  

const app = express();

  

app.enabled('trust proxy');

app.use(expressEnforceSSL());

```