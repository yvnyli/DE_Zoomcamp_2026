Query in BigQuery
```
CREATE OR REPLACE EXTERNAL TABLE `hw3_dataset.external-hw3-table`
OPTIONS (
  format = 'parquet',
  uris = ['gs://dezoomcamp_hw3_2026_yvnyli/yellow_tripdata_2024-*.parquet']
);


SELECT DISTINCT(PULocationID) FROM `hw3_dataset.hw3-table`;

SELECT DISTINCT(PULocationID) FROM `hw3_dataset.external-hw3-table`;

SELECT (PULocationID,DOLocationID) FROM `hw3_dataset.hw3-table`;



SELECT COUNT(1) FROM `hw3_dataset.hw3-table`
WHERE fare_amount = 0;


CREATE OR REPLACE TABLE `hw3_dataset.hw3-table-clusterboth`
PARTITION BY DATE(tpep_dropoff_datetime)
CLUSTER BY VendorID AS
SELECT * FROM `hw3_dataset.hw3-table`;


SELECT DISTINCT(VendorID) FROM `hw3_dataset.hw3-table`
WHERE tpep_dropoff_datetime >= TIMESTAMP('2024-03-01 00:00:00')
AND tpep_dropoff_datetime < TIMESTAMP('2024-03-16 00:00:00');


SELECT DISTINCT(VendorID) FROM `hw3_dataset.hw3-table-clusterboth`
WHERE tpep_dropoff_datetime >= TIMESTAMP('2024-03-01 00:00:00')
AND tpep_dropoff_datetime < TIMESTAMP('2024-03-16 00:00:00');

SELECT count(*) FROM `hw3_dataset.hw3-table`;
```
