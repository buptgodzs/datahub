# This "container" is a workaround to pre-create search indices
FROM jwilder/dockerize:0.6.1

RUN apk add --no-cache curl

COPY chart-index-config.json corpuser-index-config.json dashboard-index-config.json dataprocess-index-config.json dataset-index-config.json /

CMD dockerize \
    -wait http://$ELASTICSEARCH_HOST:$ELASTICSEARCH_PORT \
    -timeout 120s \
    curl -XPUT $ELASTICSEARCH_HOST:$ELASTICSEARCH_PORT/chartdocument --data @chart-index-config.json && \
    curl -XPUT $ELASTICSEARCH_HOST:$ELASTICSEARCH_PORT/corpuserinfodocument --data @corpuser-index-config.json && \
    curl -XPUT $ELASTICSEARCH_HOST:$ELASTICSEARCH_PORT/dashboarddocument --data @dashboard-index-config.json && \
    curl -XPUT $ELASTICSEARCH_HOST:$ELASTICSEARCH_PORT/dataprocessdocument --data @dataprocess-index-config.json && \
    curl -XPUT $ELASTICSEARCH_HOST:$ELASTICSEARCH_PORT/datasetdocument --data @dataset-index-config.json
