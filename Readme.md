# kafka publisher/comsumer sample

data from: https://stream.wikimedia.org/v2/stream/recentchange\

스프링 모듈로 producer/consume 생성

docker-compose.yml
<blockquote>
Kafka

```
version: '2'
services:
  zookeeper:
    image: wurstmeister/zookeeper
    container_name: zookeeper
    ports:
      - "2181:2181"
  kafka:
    image: wurstmeister/kafka
    container_name: kafka
    ports:
      - "9092:9092"
    environment:
      KAFKA_ADVERTISED_HOST_NAME: 127.0.0.1
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
```

</blockquote>


<blockquote>
Mysql

```
version: "3"
services:
  db:
    image: mysql:8.0.32-debian
    container_name: mysql-server
    ports:
      - "3306:3306"
    environment:
      MYSQL_ROOT_PASSWORD: root123
    command: # 명령어 실행
      - --character-set-server=utf8mb4
      - --collation-server=utf8mb4_unicode_ci
```

</blockquote>
