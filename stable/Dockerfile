FROM sonarsource/sonar-scanner-cli:4.3

ENV TAG=stable

LABEL image=codejamninja/node-sonar-scanner:${TAG} \
      maintainer="Jam Risser <jam@jamrizzi.com>" \
      base=alpine:3.7

RUN apk add --no-cache \
        tini

RUN cd /tmp && \
    wget http://repo1.maven.org/maven2/org/codehaus/sonar/runner/sonar-runner-dist/${SONAR_RUNNER_VERSION}/sonar-runner-dist-${SONAR_RUNNER_VERSION}.zip && \
    unzip sonar-runner-dist-${SONAR_RUNNER_VERSION}.zip && \
    cp -r /tmp/sonar-runner-${SONAR_RUNNER_VERSION}/* / && \
    cp -r /tmp/sonar-runner-${SONAR_RUNNER_VERSION}/.* / && \
    rm -rf /tmp/*

ENTRYPOINT ["/sbin/tini", "--", "/bin/sonar-runner"]
