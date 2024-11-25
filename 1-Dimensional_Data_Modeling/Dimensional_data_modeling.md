Topic about data modeling as the main output as a Data Engineer.

# Day-1
## Complex Data Types
- Struct
- Map
- Array

# Dimension
Dimension are attributes of an entity.

It helps give more context to numerical data in fact tables.

Two types of dimension:
1. Slowly-changing

Changes over time at a slow pace.

For examples:
- Address
- Favorite foods

2. Fixed

It is not change over time. Once populated, it remains static.

Examples:
- Year
- Month
- Day
- Quarter
- Countries
- States
- Cities



# Hands-on
### Load data.dump to Postgresql
- after execute `docker compose up -d`, the container will create folder "data.dump"
- copy file `data.dump` in the source repo then past to folder "data.dump
- Go to docker container terminal, then execute this command in the root dir
```bash
psql \
    -v ON_ERROR_STOP=1 \
    --username $POSTGRES_USER \
    --dbname $POSTGRES_DB \
    < /docker-entrypoint-initdb.d/data.dump/data.dump
```
- if got `error: invalid command \N` execute this in the root dir container terminal
``` bash
pg_restore -U $POSTGRES_USER -d $POSTGRES_DB data.dump/data.dump
```
