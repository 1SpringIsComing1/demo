# Running the application
- Please enter the correct credentials in twitter4j.properties file.
- Then run TwitterToKafkaServiceApplication inside IntelliJ, or run with mvn spring-boot:run command
- To use the mock tweets, set enable-mock-tweets: true in application.yml file
- Observe that we moved the TwitterToKafkaServiceConfigData to a new module called app-config-data

docker-compose -f .\common.yml -f .\kafka_cluster.yml -f ./services.yml up
docker-compose -f .\common.yml -f .\elastic_cluster.yml up
docker run -it  --network=host confluentinc/cp-kafkacat  kafkacat -b localhost:19092 -L
docker run -it  --network=host confluentinc/cp-kafkacat  kafkacat -b localhost:19092 -C -t twitter-topic

