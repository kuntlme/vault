---
tags:
  - atom
  - coding
  - help
---
```
docker run --rm -d \
  --name temp-postgres \
  -e POSTGRES_PASSWORD=devpass \
  -e POSTGRES_USER=devuser \
  -e POSTGRES_DB=devdb \
  -p 5432:5432 \
  postgres:16-alpine
```

```
postgresql://devuser:devpass@localhost:5432/devdb
```
