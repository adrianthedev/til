# Postgres

## Permissions

```sql
grant all privileges on database "avohq-v3" to "user"

ALTER SEQUENCE licenses_id_seq OWNER TO adlohrybygxdxd;

select * from pg_sequences;
GRANT USAGE, SELECT ON SEQUENCE "cities_id_seq" TO "user";

select * from pg_tables where tablename = 'accounts'
```
