# scripts_uteis

# Hercules
## Docker com HEADLESS=True

```
sudo docker-compose up --build --remove-orphans crawler_<nome_do_crawler> subscriber
```

## Celery com HEADLESS=False

```
celery -A hercules.celery_app worker -Q crawler_<NomeDaClasse> -l info -c 2
```

# Hermes

## Celery para subir workers

```
celery -A hermes worker -Q celery_hermes,hermes_Debit,hermes_Input,hermes_Integration,hermes_Output,hermes_ParseKeyworks,hermes_ParseMonaco -l info
```

## PSQL para Purge database

```
sudo su - postgres
psql
drop database hermes;
```

## PSQL para Criar database

```
sudo -u postgres createdb hermes
```

## Scripts Pandas com integração SQL

```
# Select table names
pandas.read_sql("""SELECT table_name  FROM information_schema.tables WHERE table_schema = 'public' """, connection)
```
