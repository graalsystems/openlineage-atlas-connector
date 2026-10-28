# openlineage-atlas-connector (deprecated)

> **This repository is no longer maintained and is kept for reference only.**
> The graal Data Platform now records column-level lineage in its own data catalog, and no
> longer uses Apache Pulsar or Apache Atlas. See [Data catalog](https://graal.systems/en/docs/catalog).

This was a consumer that read [OpenLineage](https://openlineage.io) events (Spark and dbt) from
an Apache Pulsar topic and created the corresponding entities in
[Apache Atlas](https://atlas.apache.org).

- `create_dbt_entity_types.py` creates the `dbt_application` and `dbt_process` entity types in Atlas.
- `consumer/store-events.py` consumes the events; it is configured with the `PULSAR_URL`,
  `PULSAR_TOPIC`, `PULSAR_SUBSCRIPTION_NAME`, `PULSAR_AUTH_TOKEN`, `ATLAS_URL`, `ATLAS_USER`
  and `ATLAS_PWD` environment variables.

```sh
python create_dbt_entity_types.py
docker build -t lineage-consumer .
docker run --env-file .env lineage-consumer
```
