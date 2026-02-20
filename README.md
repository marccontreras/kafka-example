# Kafka Twitter Streaming Example

This project demonstrates a **real-time data streaming pipeline** using **Apache Kafka** and the **Twitter API**.

The application connects to Twitter, streams live data, publishes it to a Kafka topic, and consumes the events for processing.

It is a proof-of-concept for building **event-driven architectures** and real-time data pipelines.

---

## 🧠 What This Project Demonstrates

- Real-time ingestion of external API data (Twitter)
- Publishing events to Apache Kafka
- Consuming and processing streaming data
- Basic event-driven architecture design
- Integration between Python and Kafka

---

## 🏗 Architecture Overview
Twitter API → Python Producer → Kafka Topic → Python Consumer

1. The producer connects to the Twitter API using `tweepy`
2. Incoming tweets are sent to a Kafka topic
3. The consumer subscribes to that topic and processes incoming events

---

## 🛠 Tech Stack

- Python
- Tweepy (Twitter API client)
- kafka-python
- Apache Kafka
- Zookeeper

---

## 📦 Installation

### 1️⃣ Install Python & Dependencies

Install Python from https://python.org  
Make sure to check **"Add Python to PATH"** during installation.

Install required libraries:

```bash
pip install tweepy kafka-python
```

🚀 Running Kafka Locally

Kafka requires Zookeeper.

2️⃣ Download Apache Kafka

Download the latest binary release from:

https://kafka.apache.org/downloads

Extract the archive to a directory of your choice.

3️⃣ Start Zookeeper

Navigate to the Kafka directory and run:

Linux / Mac
```bash
bin/zookeeper-server-start.sh config/zookeeper.properties
```
Windows
```bash
.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
```

4️⃣ Start Kafka Server

Open a new terminal (keep Zookeeper running):

Linux / Mac
```bash
bin/kafka-server-start.sh config/server.properties
```
Windows
```bash
.\bin\windows\kafka-server-start.bat .\config\server.properties
```

5️⃣ Create a Kafka Topic

Create the topic used by the project:

Linux / Mac
```bash
bin/kafka-topics.sh --create \
--topic rk_hadoop \
--bootstrap-server localhost:9092 \
--partitions 1 \
--replication-factor 1
```

Windows
```bash
.\bin\windows\kafka-topics.bat --create \
--topic rk_hadoop \
--bootstrap-server localhost:9092 \
--partitions 1 \
--replication-factor 1
```

▶ Running the Application

Make sure:

Kafka is running

Zookeeper is running

The topic rk_hadoop exists

Twitter API credentials are correctly configured in the script

Then run:
```bash
python nombre_del_archivo.py
```

If everything is configured correctly:

The application connects to Twitter

Streams tweets in real time

Publishes them to Kafka

Consumes and prints them to the console

🔥 Possible Improvements

To make this project production-ready:

Add Docker Compose for Kafka setup

Externalize Twitter credentials using environment variables

Add structured logging

Implement error handling & retries

Add dead-letter queue (DLQ)

Add unit and integration tests

📌 Use Case Inspiration

This pattern can be used for:

Real-time sentiment analysis

Event-driven microservices

Financial data streaming

Fraud detection systems

Social media analytics pipelines
