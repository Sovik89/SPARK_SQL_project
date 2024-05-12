# SPARK_SQL_project with DataProc <br />
 <br />
  <br />
SPARK SQL Project to convert csv files for NYSE data to parquet file with partition key as trademonth(YYYYmm). The target table or the golden data is created using Delta table using DeltaLake combining with spark SQL.
Also depicting the shortcomings of SPARK sql comparing with HIVE SQL.

## Steps for data loading from hdfs golden location to gcs bucket hence consumed by GBQ<br/>
<br />
1. <b>create separate bucket</b><br />
2. <b>create dataset and corresponding table<b/><br />

3. from cluster command prompt-><b>hadoop distcp hdfs://cluster-2fef-sovik-m/user/hive/warehouse/retail_db.db/orders gs://sovik-big-query-bucket-1/orders</b><br />

4. Load in Big Query: <b>bq load --autodetect --source_format=PARQUET orders.orders_v2 gs://sovik-big-query-bucket-1/orders/orders/part-*</b>
