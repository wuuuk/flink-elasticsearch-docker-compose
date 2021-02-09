FROM flink:1.11.1-scala_2.11

COPY sql-client/ /opt/sql-client
RUN mkdir -p /opt/sql-client/lib

COPY lib/flink-json-1.11.1.jar /opt/sql-client/lib/
COPY lib/flink-sql-connector-kafka_2.11-1.11.1.jar /opt/sql-client/lib/
COPY lib/flink-sql-connector-elasticsearch7_2.11-1.11.1.jar /opt/sql-client/lib/
COPY lib/flink-connector-jdbc_2.11-1.11.1.jar /opt/sql-client/lib/
COPY lib/mysql-connector-java-8.0.23.jar /opt/sql-client/lib/
COPY lib/flink-connector-mysql-cdc-1.1.1.jar /opt/sql-client/lib/
COPY conf/* /opt/flink/conf/

WORKDIR /opt/sql-client
ENV SQL_CLIENT_HOME /opt/sql-client

COPY docker-entrypoint.sh /
ENTRYPOINT ["/docker-entrypoint.sh"]
