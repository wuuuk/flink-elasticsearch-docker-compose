FROM wuuuk/flink:latest

WORKDIR /opt/sql-client
RUN mv /opt/flink/lib /opt/sql-client
COPY sql-client/ /opt/sql-client
COPY conf/* /opt/flink/conf/
COPY docker-entrypoint.sh /
ENV SQL_CLIENT_HOME /opt/sql-client
ENTRYPOINT ["/docker-entrypoint.sh"]
