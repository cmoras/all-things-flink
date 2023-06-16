FROM  apache/flink-kubernetes-operator:latest
ENV FLINK_PLUGINS_DIR=/opt/flink/plugins
RUN mkdir $FLINK_PLUGINS_DIR/s3-fs-presto
COPY ./flink-s3-fs-presto-1.15.0.jar $FLINK_PLUGINS_DIR/s3-fs-presto/
