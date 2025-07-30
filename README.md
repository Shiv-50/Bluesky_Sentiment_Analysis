# Bluesky_Sentiment_Analysis

start zookeeper
start kafka
start hbase

#on terminal 1:
#run spark consumer for live sentiment prediction
spark-submit  --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.4.1 scripts/spark_to_hdfs.py

#on terminal 2 :
python kafka_to_hdfs.py

#on terminal 4: (Run after all above scripts and servers are running)
#run to get access token 
bash bluesky_access_token.txt 
#send query requests
bash kafka_producer.txt

hdfs dfs -getmerge /user/spark/bluesky_data /user/spark/bluesky_data/all_data.csv
