FROM centos

ARG BUILD_DATE
ARG BUILD_VERSION
ARG COMPOSE
ARG K8SYML

LABEL org.opencontainers.image.authors="clemenko@gmail.com" \
      org.opencontainers.image.source="https://github.com/clemenko/dockerfiles/tree/master/demo_flask" \
      org.opencontainers.image.created=$BUILD_DATE \
      org.opencontainers.image.title="clemenko/flask_demo" \
      org.opencontainers.image.description="The repository contains a simple flask application " \
      org.opencontainers.image.build="docker build -t clemenko/flask_demo --build-arg BUILD_DATE=$(date +%D) --build-arg BUILD_VERSION=0.01 --build-arg COMPOSE=$(cat ../../compose/flask_demo.yml|base64)  --build-arg K8SYML=$(cat ../../k8s_yaml/k8s_all_the_things.yml|base64) . " \
      org.opencontainers.image.source=$BUILD_VERSION \
      org.zdocker.compose=$COMPOSE \
      org.zdocker.k8s=$K8SYML

RUN yum update -y && \
      rpm -e --nodeps rpm rpm-build-libs rpm-libs python3-rpm yum $(rpm -qa *dnf*) python3-hawkey && \
      rm -rf /var/cache/yum /var/cache/dnf
    
CMD ["echo", "hello"]
