<h1 align="center">
  Streaming Data Pipeline - Kafka + ELK Stack
</h1>

Streaming weather data using Apache Kafka and Elastic Stack.

Data source: https://openweathermap.org/api

Objectives: Develop a streaming data pipeline to extract weather data from OpenWeather API using Apache Kafka, Logstash, Elasticserach and Kibana (Kafka + ELK Stack).


<p align="center">
  <img width="830" alt="Screen Shot 2021-11-11 at 17 46 57" src="https://github.com/felipedmnq/Stream-Kafka-ELK-Stack/blob/master/images/Screen%20Shot%202022-01-03%20at%2018.45.18.png?raw=true">
</p>

To summarize, Python was used to develop a Kakfa producer that requests weather data from OpenWeather API every minute and sends it as a message to Apache Kafka. Logstash, as a Kafka consumer, consumes the data and stores it into Elasticsearch. Kibana uses the data from Elasticsearch to display the dashboard.

<h3 align="center">
  Kibana Weather Dashboard
</h3>

<p align="center">
  <img width="830" alt="Screen Shot 2021-11-11 at 17 46 57" src="https://github.com/felipedmnq/Stream-Kafka-ELK-Stack/blob/master/images/2022-01-03%2018.56.44.gif?raw=true">
</p>

#### Steps:
  - `bash elk/start_elastic_docker.sh`
  - `bash kafka/start_kafka_docker.sh`
  - Create a topic using kafka manager: `localhost:9000`
  
  Logstash installed locally*
  - `$LOGSTASH_HOME/bin/logstash -f $LOGSTASH_HOME/config/pipeline.conf`
  
  Before running Kafka Producer, is needed to set the API key inside the `weather_api_key.ini` file*
  - `python3 weather_kfk_producer.py`
  - Access Kibana: `localhost:5601`
  - Create an index pattern: must match with your index name inside `pipeline.conf`
  - Develop your dashboard.
