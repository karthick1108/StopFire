# Spark-Streaming-Application
Build a complete setup from streaming to storing and analyzing the data using Apache Kafka, Apache Spark Streaming and MongoDB.

Datasets folders contains data that are used for this assignment

Task 1. Design a suitable data model to support the efficient querying of the two data sets(hotspot_historic.csv and climate_historic.csv) in MongoDB and Querying MongoDB using PyMongo

Task 2. Processing Data Stream - In this task, I've Implemented multiple Apache Kafka producers to simulate the real-time streaming of the data which will be processed by Apache Spark Streaming client and inserted into MongoDB.

Task 2.1 Event Producer 1 - Python program that loads all the data from climate_streaming.csv and randomly feed the data to the stream every 5 seconds. I've also appended additional information such as sender_id and created_time.

Task 2.2 Event Producer 2 - Python program that loads all the data from hotspot_AQUA_streaming.csv and randomly feed the data to the stream every 10 - 30 seconds. AQUA is the satellite from NASA that reports latitude, longitude, confidence and surface temperature of a location. I've also appended additional information such as sender_id and created_time

Task 2.3 Event Producer 3 - Python program that loads all the data from hotspot_TERRA_streaming.csv and randomly feed the data to the stream every 10 - 30 seconds. TERRA is another satellite from NASA that reports latitude, longitude, confidence and surface temperature of a location. I've also appended additional information such as sender_id and created_time

Task 3. Streaming Application - Streaming application in Apache Spark Streaming which has a local streaming context with two execution threads and a batch interval of 10 seconds. The streaming application will receive streaming data from all three producers. If the streaming application has data from all or at least two of the producers, data will be processed as follows:

#1 Streams will be joined based on the location (i,e, latitude and longitude) and data model is developed like the one I created in Task 1.

#2 Determine whether 2 streams are close to each other. To implement this I have used geo-hashing algorithm with precision 5. The precision determines the number of characters in the Geohash.

#3 If we receive the data from two different satellites AQUA and TERRA for the same location, then average the ‘surface temperature’ and ‘confidence’.

#4 If the streaming application has the data from only one producer (Producer 1), it implies that there was no fire at that time and we can store the climate data into MongoDB straight away.

Task 4. Data Visualization using Matplotlib
