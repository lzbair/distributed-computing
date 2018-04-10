### Run zookepper:
./run/bin/zookeeper-server-start.sh ./run/config/zookeeper.properties

### Run kafka broker:
./run/bin/kafka-server-start.sh ./run/config/server.properties

### Run java main:
io.streams.wordcount.WordCount#main

## Play:
### Run the producer in a separate console
./run/bin/kafka-console-producer.sh --broker-list localhost:9092 --topic streams-plaintext-input  

### Run the consumer in a separate console
kafka-console-consumer.bat --bootstrap-server localhost:9092   
                           --topic streams-wordcount-output   
						   --from-beginning 
						   --formatter kafka.tools.DefaultMessageFormatter   
						   --property print.key=true   
						   --property print.value=true   
						   --property key.deserializer=org.apache.kafka.common.serialization.StringDeserializer   
						   --property value.deserializer=org.apache.kafka.common.serialization.LongDeserializer  
						   
(write some texts on producer console, then check the words count on consumer console)
