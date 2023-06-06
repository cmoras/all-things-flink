FROM flink:1.15

WORKDIR /opt/flink

RUN mv examples/streaming/TopSpeedWindowing.jar lib/

RUN chown -R flink:flink .


ENTRYPOINT ["/docker-entrypoint.sh"]
EXPOSE 6123 8081
CMD ["help"]
