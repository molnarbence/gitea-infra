# gitea-infra

## Migrate to new instance

Exec `pg_dumpall` on the old instance:
```sh
docker exec gitea-postgres-old pg_dumpall -U gitea > dump.sql
```

Move the `dump.sql` to the data folder of the new instance

Exec `bash` on the new instance
```sh
docker exec -it gitea-postgres-new bash
```

Read the `dump.sql` file into the database

```sh
psql -U gitea < dump.sql
```