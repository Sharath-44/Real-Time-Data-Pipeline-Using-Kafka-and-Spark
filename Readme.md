# Real-Time Data Pipeline Using Kafka and Spark

## Overview

This project demonstrates a real-time data pipeline using Apache Kafka for messaging and Apache Spark for stream processing. It simulates temperature sensor data being collected in real-time and processed for various analytics.

## Motivation

Real-time data processing is crucial in today's data-driven world, where organizations need to make quick decisions based on the latest information. This project aims to demonstrate how a scalable and fault-tolerant data pipeline can be built using open-source tools like Kafka and Spark.

## Key Components

- **Apache Kafka**: Kafka is a distributed streaming platform that provides publish-subscribe messaging capabilities. It allows data to be ingested from multiple sources and processed in real-time.
  
- **Apache Spark**: Spark is a fast and general-purpose distributed computing engine for large-scale data processing. It provides high-level APIs in Scala, Java, Python, and R, and supports real-time stream processing, batch processing, and machine learning.

- **MongoDB**: MongoDB is a NoSQL database that stores the processed sensor data. It provides flexibility and scalability for handling large volumes of data generated by real-time applications.

## Data pipeline architecture

![Data pipeline architecture](<WhatsApp Image 2024-04-21 at 15.02.02_19daff5c.jpg>)

## Requirements

- PySpark 3.5.1
- Apache Kafka 3.7.0
- Apache Spark 3.5.1
- MongoDB 7.0.8

## Installation

1. Clone the repository to your local machine.
2. Install and configure Apache Kafka and Apache Spark.
3. Install MongoDB and ensure it's running.

## How to run

1. Start Zookeeper: `bin/zookeeper-server-start.sh config/zookeeper.properties`
2. Start Kafka: `bin/kafka-server-start.sh config/server.properties`
3. Create Kafka topics:
    - RawSensorData topic:
        ```
        bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic RawSensorData
        ```
    - ValidatedSensorData topic:
        ```
        bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic ValidatedSensorData
        ```
    - CleanSensorData topic:
        ```
        bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic CleanSensorData
        ```

5. Run `python sensor.py` to start generating sensor data.
6. Run `python push_data_to_kafka.py`
7. Structure and Validate Data, Push To MongoDB and Kafka Topic CleanSensorData: `./bin/spark-submit structure_validate_store.py`
8. Real-Time Dashboard - Visualization: `bokeh serve --show dashboard.py`

## Contributors

- [Sharath M S](https://github.com/Sharath-44)
- Aditya Vishwanatha
- [Sahana Parasuram](https://github.com/sahanaparasuram)
- [Saransh Mehta](https://github.com/mehtasaransh11)
