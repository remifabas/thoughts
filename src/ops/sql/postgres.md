# Postgres

```bash
docker run -d --name my-postgres -e POSTGRES_PASSWORD=postgres -e POSTGRES_USER=postgres -e POSTGRES_DB=goods -p 5432:5432 postgres:15.2

docker exec -it postgresql psql -d goods -U postgres
```

```sql
CREATE TABLE goods(
    id BIGSERIAL NOT NULL PRIMARY KEY ,
    name VARCHAR(255) NOT NULL,
    description TEXT NULL,
    price INT NOT NULL
);

INSERT INTO goods (name, description, price)
VALUES ('Apple', 'Red fruit', 100),
       ('Orange', 'Orange fruit', 150),
       ('Banana', 'Yellow fruit', 200),
       ('Pineapple', 'Yellow fruit', 250),
       ('Melon', 'Green fruit', 300);
```
