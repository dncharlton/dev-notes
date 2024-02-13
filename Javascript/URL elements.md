---
tags:
  - webdev
  - url
  - javascript
  - theory
---
Parts of a URL:
```
- The protocol is required
- Usernames and passwords are optional
- A domain is required
- The default port for a given protocol is used if one is not provided
- The default (`/`) path is used if one isn't provided
- A query is optional
- A fragment is optional
```

![[URL Elements.png]]

E.g:
`http://testuser:testpass@testdomain.com:8080/testpath?testsearch=testvalue#testhash

```
protocol: http:
username: testuser
password: testpass
hostname: testdomain.com
port: 8080
pathname: /testpath
search: ?testsearch=testvalue
hash: #testhash
```


