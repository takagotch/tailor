### tailor
---
https://github.com/zalando/tailor

```
yarn add node-tailor

git clone https://github.com/zalando/tailor.git
cd tailor
yarn
```

```js
const http = require('http');
const Tailor = require('node-tailor');
const tailor = new Tailor({/**/});
const server = http.createServer(tailor.requestHandler);
server.listen(process.env.PORT || 8080);

http
  .createServer((req, res) => {
    req.headers['x-request-uri'] = req.url
    req.url = '/index'
    tailor.requestHandler(req, res);
  })
  .listen(8080, function(){
    console.log('Tailor server listening on port 8080');
  });
```

```
<html>
<head>
  <script type="fragment" src="http://assets.domain.com"></script>
</head>
<body>
  <fragment src="http://header.domain.com"></fragment>
  <fragment src="http://content.domain.com"></fragment>
  <fragment src="http://footer.domain.com"></fragment>
</body>
</html>
```

