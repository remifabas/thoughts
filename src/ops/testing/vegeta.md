# Vegeta

```bash
vegeta attack -targets conf.txt -name=5000qps -rate=5000 -duration=1s > result.js.bin
```

Simple GET request

```
GET http://localhost:8080/goods
```

POST with body Example of conf.txt

```
POST http://localhost:8082/api/graphql
Authorization: Bearer ..
content-type: application/json
@body.json
```

Example of body.json

```json
{
  "query": "query{\n  rmfs(){\n    edges{\n      node{\n        id\n        name\n      }\n    }\n  }\n}"
}
```
