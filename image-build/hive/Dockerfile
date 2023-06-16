FROM flink:1.16.2@sha256:d836ec8670b74308df5300e48da1905d09c075cbdcf64ef77af3cc28593fceb9

WORKDIR /opt/flink

# Create the hive-conf directory
RUN mkdir -p /opt/flink/hive-conf
COPY flink-hive-config.yaml /opt/flink/hive-conf
RUN ls conf/

# Move flink-table-planner JAR to lib directory
RUN mv $FLINK_HOME/opt/flink-table-planner_2.12-1.16.2.jar $FLINK_HOME/lib/flink-table-planner_2.12-1.16.2.jar

# Move flink-table-planner-loader JAR out of lib directory
RUN mv $FLINK_HOME/lib/flink-table-planner-loader-1.16.2.jar $FLINK_HOME/opt/flink-table-planner-loader-1.16.2.jar

# Download and include Hive dependencies
RUN wget -O $FLINK_HOME/lib/flink-connector-hive_2.12-1.16.2.jar https://repo1.maven.org/maven2/org/apache/flink/flink-connector-hive_2.12/1.16.2/flink-connector-hive_2.12-1.16.2.jar && \
    wget -O $FLINK_HOME/lib/hive-exec-3.1.0.jar https://repo1.maven.org/maven2/org/apache/hive/hive-exec/3.1.0/hive-exec-3.1.0.jar && \
    wget -O $FLINK_HOME/lib/libfb303-0.9.3.jar https://repo1.maven.org/maven2/org/apache/thrift/libfb303/0.9.3/libfb303-0.9.3.jar && \
    wget -O $FLINK_HOME/lib/antlr-runtime-3.5.2.jar https://repo.maven.apache.org/maven2/org/antlr/antlr-runtime/3.5.2/antlr-runtime-3.5.2.jar && \
    wget -O $FLINK_HOME/lib/flink-sql-connector-hive-3.1.2_2.12-1.16.2.jar https://repo.maven.apache.org/maven2/org/apache/flink/flink-sql-connector-hive-3.1.2_2.12/1.16.2/flink-sql-connector-hive-3.1.2_2.12-1.16.2.jar


RUN wget -O $FLINK_HOME/lib/hadoop-common-3.2.0.jar https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-common/3.2.0/hadoop-common-3.2.0.jar


