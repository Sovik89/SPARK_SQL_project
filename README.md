# SPARK_SQL_project with DataProc <br />
 <br />
  <br />
SPARK SQL Project to convert csv files for NYSE data to parquet file with partition key as trademonth(YYYYmm). The target table or the golden data is created using Delta table using DeltaLake combining with spark SQL.
Also depicting the shortcomings of SPARK sql comparing with HIVE SQL.

# Steps for data loading from hdfs golden location to gcs bucket hence consumed by GBQ<br/>
<br />
1. create separate bucket<br />
2. create dataset and corresponding table<br />

3. from cluster command prompt->hadoop distcp hdfs://cluster-2fef-sovik-m/user/hive/warehouse/retail_db.db/orders gs://sovik-big-query-bucket-1/orders<br />

4. Load in Big Query: bq load --autodetect --source_format=PARQUET orders.orders_v2 gs://sovik-big-query-bucket-1/orders/orders/part-*
