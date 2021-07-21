Tags: #restapi

---

# CURL

## Overview

### Verbose

```
$ curl -v http://example.com/index.html
```

### Output

```
$ curl -o out.json http://example.com/index.html
```

## HTTP Methods with curl

### GET

```
$curl -v http://localhost:3000/auth/me
```

### POST

```
$ curl -d "username=example&email=example@gmail.com" http://localhost:3000/user/new
```

or alternatively, pass a file containing the request body to the data option

```
$ curl -d @request.json -H "Content-Type: application/json" http://localhost:3000/user/new
```

### PUT

```
$ curl -d @request.json -H "Content-Type: application/json" -X PUT http://localhost:3000/user/dangvanthanh/14
```

### DELETE

```
$ curl -x DELETE http://localhost:3000/user/dangvanthanh/14

```