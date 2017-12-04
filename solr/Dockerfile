FROM solr:7.1.0-alpine

ENV CORES singleapp_staging singleapp_production singleapp_development

USER root

ADD ./configsets/sample /opt/solr/server/solr/configsets/sample
RUN chown 8983:8983 -R /opt/solr/server/solr/configsets/sample

USER solr

RUN solr start &&\
    for core in ${CORES}; do\
      solr create_core -c ${core} -d /opt/solr/server/solr/configsets/sample;\
    done &&\
    solr stop
