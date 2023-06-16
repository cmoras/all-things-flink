# Use the Flink base image
FROM flink:1.10.0-scala_2.11

# Create directories for Presto and Hadoop connectors
RUN mkdir /opt/flink/plugins/s3-fs-presto
RUN mkdir /opt/flink/plugins/s3-fs-hadoop
RUN mkdir /opt/flink/hive-config

# Download flink-s3-fs-presto JAR
RUN wget -P /opt/flink/plugins/s3-fs-presto \
    https://repo.maven.apache.org/maven2/org/apache/flink/flink-s3-fs-presto/1.10.0/flink-s3-fs-presto-1.10.0.jar

# Download flink-s3-fs-hadoop JAR
RUN wget -P /opt/flink/plugins/s3-fs-hadoop \
    https://repo.maven.apache.org/maven2/org/apache/flink/flink-s3-fs-hadoop/1.10.0/flink-s3-fs-hadoop-1.10.0.jar


ADD VERSION .

# Download connector libraries
RUN wget -P /opt/flink/lib/ https://repo.maven.apache.org/maven2/org/apache/flink/flink-json/${FLINK_VERSION}/flink-json-${FLINK_VERSION}.jar; \
    wget -P /opt/flink/lib/ https://repo.maven.apache.org/maven2/org/apache/flink/flink-sql-connector-kafka_2.11/${FLINK_VERSION}/flink-sql-connector-kafka_2.11-${FLINK_VERSION}.jar; \
    wget -P /opt/flink/lib/ https://repo.maven.apache.org/maven2/org/apache/flink/flink-jdbc_2.11/1.10.0/flink-jdbc_2.11-1.10.0.jar; \
    wget -P /opt/flink/lib/ https://repo.maven.apache.org/maven2/org/apache/flink/flink-csv/1.10.0/flink-csv-1.10.0.jar; \
    wget -P /opt/flink/lib/ https://repo.maven.apache.org/maven2/mysql/mysql-connector-java/8.0.19/mysql-connector-java-8.0.19.jar;

# Download Hive dependencies
RUN wget -P /opt/flink/lib https://repo.maven.apache.org/maven2/org/apache/flink/flink-connector-hive_2.11/1.10.0/flink-connector-hive_2.11-1.10.0.jar; \
    wget -P /opt/flink/lib https://repo.maven.apache.org/maven2/org/apache/hive/hive-exec/2.3.6/hive-exec-2.3.6.jar;

# get Hadoop for Hive
RUN wget -P /opt/flink/lib https://repo.maven.apache.org/maven2/org/apache/flink/flink-shaded-hadoop-2-uber/2.7.5-8.0/flink-shaded-hadoop-2-uber-2.7.5-8.0.jar;

# Copy configuration
COPY conf/sql-client-conf.yaml /opt/flink/hive-config
COPY hive-conf/* /opt/flink/hive-config


