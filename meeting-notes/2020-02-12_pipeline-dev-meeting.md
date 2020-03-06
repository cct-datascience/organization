# Dashboards & monitoring

## Meeting

2020-02-12

Present: Max, Emily, Julian

#### Julian's Notes

- Monitoring & logging hard to stay on stop with at scale
- Easier to just retry & make transformers idempotent?

- [ ] Talk to Eric/David about whether we need to tar the products/output of
Makeflow steps (in addition to raw input data)

- Look at TimescaleDB
    - Ideally store plaintext metadata with files so we can regenerate database

- Catcher's Mitt: Thing that triggers processing/tarring
- Pull data to ds06
    - Globus - going away soon because NCSA
     will not be processing any more data and are trying to get the data off
     their servers. (According to Max)
- How to know a scan is done?
    - **UPDATE 2020-03-06:** While visiting the gantry (2020-02-28) we talked to Jeffrey about getting access to the raw CSV of the scan log. See [Google sheet of scan log](https://docs.google.com/spreadsheets/d/1dZYE6UbF9rmYuUNLkpUNJzXkc7kHPAZhoBxQtGuCUXc/edit?usp=sharing)
    - Look at Google doc from when Rob & Max were in town
    - Look at scan IDs
    - Pull in order of ascending scan IDs

Visualizations for Dashboard:

1. Raw data: Transfer/throughput (primarily collection, not processing)
2. Derived data: How many products generated per type/per day

#### Max's Notes

2020 TERRA-OPEN REDESIGN

File monitoring - Postgres DB
- Entries for files arriving via Globus
- Path, size, timestamp, sensor, season, date, scan
- Processing status (arrived, submitted to workflow, completed, uploaded…)

Derived files
- Parent file
  - This could drive the 'filecounter' page I use through a database instead of filesystem counting
- View with daily aggregations?
- How does this interact with tar archives?
  - Include an archive field
- Psql append-only with date-based indexing
  - timescaleDB
  - Workflow monitoring

Does this make sense in Makeflow context?
- Rulechecker probably goes away (used to count full field readiness)

Capture of errors with terra-logging but overwhelming volume, value in troubleshooting was relatively low

Replace with basic monitoring of VMs?
- Clowder, Mongo, Elasticsearch, processing nodes
- Responding? CPU/memory load?

#### Dashboard
- Grouped by sensor + season, see daily amounts of each product
- Some wiring so dashboard knows product lineage (e.g. raw->bin2tif->rgbmask->canopycover)
  - Makeflow metadata about workflow, version, etc.
- Interactive elements for submission of missing stuff?
- Aggregations like daily processing rates, etc. Again this changes with Makeflow.
  - How much have we transferred per sensor per day?
- Plot-based tracking
  - What is our plot coverage per day
