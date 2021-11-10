# Real-time Tables in Apache Pinot

In this example, we're going to ingest events into Apache Pinot from the [Wikipedia Event Platform](https://wikitech.wikimedia.org/wiki/Event_Platform/EventStreams#JavaScript)

⭐️ Create a Schema for the Events  
⭐️ Create a Real-time Table  
⭐️ Send events to Pinot through Apache Kafka  
🚀 Query the Events in Real-time

# Guide

Install Node and npm:

```bash
curl -fsSL https://deb.nodesource.com/setup_14.x | bash -
apt install nodejs
```

Install vim:

```bash
apt install vim
```

Install Apache Kafka:

```
wget https://dlcdn.apache.org/kafka/3.0.0/kafka_2.13-3.0.0.tgz
tar -xvf kafka_2.13-3.0.0.tgz
mv kafka_2.13-3.0.0 kafka
rm -rf kafka_2.13-3.0.0.tgz
```

Edit the server properties for Kafka found in `kafka/config/server.properties`.
Change `zookeeper.connect` to `localhost:2181/kafka`.

Start Kafka:

```
./bin/kafka-server-start.sh config/server.properties
```

Create folders for real-time data. From `/app` run:

```
mkdir realtime
cd realtime
mkdir events
```

Copy the `wikievents.js` file from this repo to `/app/realtime/wikievents.js`.

Install the dependencies for `wikievents.js`:

```
npm i eventsource kafkajs
```

Run `wikievents.js` to start the event stream.

```
node wikievents.js
```

Create the Schema for the events in Pinot using the `realtime.schema.json`.
Create the Table using the `realtime.tableconfig.json`.

Add the Schema:

```
./pinot/bin/pinot-admin.sh AddSchema -schemaFile ./realtime/realtime.schema.json -exec
```

Add the Table:

```
./pinot/bin/pinot-admin.sh AddTable -tableConfigFile ./realtime/realtime.tableconfig.json -exec
```

Now you can query the table as the events are coming in!
