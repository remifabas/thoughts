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


## ramp up
``` bash
echo "GET <http://:6060>" | ./vegeta attack -timeout=6s -duration=20s -plan="100@2s 200@4s 400@6s 500@8s 600@10s" | tee result.bin | ./vegeta report
```