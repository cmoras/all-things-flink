FROM flink:1.16.2@sha256:d836ec8670b74308df5300e48da1905d09c075cbdcf64ef77af3cc28593fceb9

WORKDIR /opt/flink

# Create the hive-conf directory
RUN mkdir -p /opt/flink/hive-conf
COPY flink-hive-config.yaml /opt/flink/hive-conf

RUN ls -lah /opt/flink/conf/

# Move flink-table-planner JAR to lib directory
RUN mv $FLINK_HOME/opt/flink-table-planner_2.12-1.16.2.jar $FLINK_HOME/lib/flink-table-planner_2.12-1.16.2.jar

# Move flink-table-planner-loader JAR out of lib directory
RUN mv $FLINK_HOME/lib/flink-table-planner-loader-1.16.2.jar $FLINK_HOME/opt/flink-table-planner-loader-1.16.2.jar

RUN wget -O $FLINK_HOME/lib/hadoop-common-3.2.0.jar https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-common/3.2.0/hadoop-common-3.2.0.jar && \
    wget -O $FLINK_HOME/lib/hadoop-hdfs-3.2.0.jar https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-hdfs/3.2.0/hadoop-hdfs-3.2.0.jar && \
    wget -O $FLINK_HOME/lib/hadoop-yarn-common-3.2.0.jar https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-yarn-common/3.2.0/hadoop-yarn-common-3.2.0.jar


RUN ls  ./
