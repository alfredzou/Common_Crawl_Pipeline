# Common Crawl Pipeline
Common Crawl maintains a free, open repository of web crawl data. This data is released roughly every 2 months.

For the November/December dataset, the data was crawled between November 28th and December 12th, and contains 3.35 billion web pages (or 454 TiB of uncompressed content).

This represents a huge amount of data and is perfect for practicing a big data mindset. The aim will be to download and ingest the data into BigQuery then perform some simple transformations using PySpark.

https://commoncrawl.org/get-started

Due to the volume of the data some key considerations are:
* how to store the data. Does it make sense to store in GCS?
* how to ingest the data
* how to be cost efficient (what is the cost of storage per month)
* how to optimise analytics on the data (clustering, partitioning, what is the cost of a query)

# Technologies Plan
* PySpark (download & transformation)
* Dataproc (spark cluster)
* BigQuery (storage, clustering and partitioning)
* GCS (data lake)
* Terraform spin up DataProc, BigQuery, GCS, Mage
* Some library to open WARC, WET and WAT files
* Mage

# High level plan
* Check the data and see what we want to keep
* Terraform set up infrastructure
* Set up ingestion script to dl data

# Pipelines
* check pipeline to check if new data, if so dl new paths files, if new paths file trigger actual ETL pipeline
* ETL pipeline ingest data by iterating through paths to dl (maybe there will be an issue with mage)
    * Store/stage in GCS?
    * Transform and store in BigQuery
