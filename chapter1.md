# Kafka

[https://kafka.apache.org/](https://kafka.apache.org/)

A distributed streaming platform.

1. can be used as an enterprise messaging system
2. can be used it as a stream processing platform. Kafka gives a stream, and we can plug in a processing framework.
3. Also provides connectors to export and import bulk data from databases and other systems.

[https://kafka.apache.org/images/kafka\_diagram.png](https://kafka.apache.org/images/kafka\_diagram.png)

Install/Unzip Apache Kafka

```
tar -zxvf kafka_2.11-0.10.1.0.tgz
```

Start Kafka Server

```
bin/zookeeper-server-start.sh config/zookeeper.properties
```

```
bin/kafka-server-start.sh config/server.properties
```

kafka-topics.sh is a tool to manage a Kafka

Create Kafka Topic (replication factor 3, and 2 partitions)

```
bin/kafka-topics.sh --zookeeper localhost:2181 --create --topic TopicName --partitions 2 --replication-factor 2
```

describe Kafka Topic

```
bin/kafka-topics.sh --zookeeper localhost:2181 --describe --topic TopicName
```

* _ISR is a list of In Sync Replicas_

Start Kafka Producer and Consumer

console producer

```
bin/kafka-console-producer.sh --broker-list localhost:9092 --topic TopicName
```

console consumer

```
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic TopicName
```

Broker Configurations

```
// 3 essential configurations are the following:

broker.id
port
log.dirs
```

```
zookeeper.connect
delete.topic.enable
auto.create.topics.enable
default.replication.factor
num.partitions
log.retention.ms
log.retention.bytes
```

complete list : [https://kafka.apache.org/documentation/#brokerconfigs](https://kafka.apache.org/documentation/#brokerconfigs)

Build.sbt

```
    name := "KafkaTest"

    libraryDependencies ++= Seq(
        "org.apache.kafka" % "kafka-clients" % "0.10.1.0"
        exclude("javax.jms", "jms")
        exclude("com.sun.jdmk", "jmxtools")
        exclude("com.sun.jmx", "jmxri")
        exclude("org.slf4j", "slf4j-simple")
    )
```

Simple Kafka producer

```
import java.util.*;
    import org.apache.kafka.clients.producer.*;                                    
    public class TestProducer {                                    
            public static void main(String[] args) throws Exception{

                String key = "Key1";                
                String value = "Value1";
                String topicName = "KafkaTestTopic";

                Properties props = new Properties();                
                props.put("bootstrap.servers", "localhost:9092,localhost:9093");
                props.put("key.serializer","org.apache.kafka.common.serialization.StringSerializer");         
                props.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer");

                Producer producer = new KafkaProducer<>(props);
                ProducerRecord record = new ProducerRecord<>(topicName,key,value);

                producer.send(record);                
                producer.close();
        }
    }
```
