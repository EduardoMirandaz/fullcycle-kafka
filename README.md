Precisamos de criar os brokers(kafkas) e os clusters se necessário.
Para isso, podemos pegar imagens prontas do docker e utilizar, como por exemplo as presentes em https://github.com/confluentinc/cp-docker-images

Com o Kafka-Cluster-Example

Devemos prosseguir da seguinte forma:

rodamos o 
docker-compose up -d
rodamos o docker-compose ps para validar que nossos zookeepers e nossos kafkas(brokers) foram criados.

em seguida, para entrar dentor de uma de nossas máquinas, utilizamos o 
docker exec -it <nome_do_kafka_listado_no_ps> bash, ao pressionar enter, entramos no nosso kafka!

Para criar tópicos, podemos rodar, dentro do kafka:
kafka-topics --create --bootstrap-server localhost:29092 --replication-factor 2 --partitions 3 --topic meu-topico
 

(replication factor(quantas réplicas das partições desse tópico teremos espalhadas nas outras portas?)

para listar os criados, rodamos:

kafka-topics --list --bootstrap-server localhost:29092

Podemos manipular o consumidor e o produtor por um console do próprio kafka

Para o produtor:

kafka-console-producer --broker-list localhost:29092 --topic meu-topico

Para o consumidor (em outro terminal, e dentro do mesmo tópico)(só dar o docker exec de novo)

kafka-console consumer --broker-list localhost:29092 --topic meu-topico

