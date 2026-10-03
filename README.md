# parking_dbt — bronze → silver → gold demo (dbt-trino + Iceberg)

    bronze.ticket ──► silver.slv_ticket (incremental merge, dedup, clean)
                         ├─► gold.gld_daily_park_revenue
                         ├─► gold.gld_hourly_traffic
                         └─► gold.gld_vehicle_type_monthly

## Run
    pip install -r requirements.txt   # dbt-core 1.11 + dbt-trino (needs dbt-core >= 1.8)
    cp profiles.yml.example ~/.dbt/profiles.yml   # edit host/auth
    dbt debug
    dbt build                      # run + test
    dbt build --full-refresh       # rebuild silver from scratch
    dbt docs generate && dbt docs serve   # lineage graph for the demo
