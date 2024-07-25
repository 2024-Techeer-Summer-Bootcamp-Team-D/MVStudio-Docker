ARG ELASTIC_VERSION

# https://www.docker.elastic.co/
FROM docker.elastic.co/elasticsearch/elasticsearch:${ELASTIC_VERSION}

# Nori 플러그인 설치
RUN elasticsearch-plugin install analysis-nori

# Elasticsearch를 시작
CMD ["elasticsearch"]