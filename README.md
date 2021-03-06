# jboss-wildfly [![Build Status](https://travis-ci.org/daggerok/jboss-wildfly.svg?branch=master)](https://travis-ci.org/daggerok/jboss-wildfly)

## DEPRECATED

### USE [daggerok](https://github.com/daggerok/jboss)/[jboss:wildfly-12.0.0.Final](https://hub.docker.com/r/daggerok/jboss) instead

JBOSS WildFly 11.0.0.Final docker image (Linux Alpine, OpenJDK 8u151)

**Exposed ports**:

- 8080 - deployed apps
- 9990 - console
- 8443 - https

**Console**:

- url: http://127.0.0.1:9990/console
- user: admin
- password: Admin.123

### Usage:

```

FROM daggerok/jboss-wildfly:11.0.0.Final
ADD ./build/libs/*.war ${JBOSS_HOME}/standalone/deployments/
```

#### Remote debug:

```

FROM daggerok/jboss-wildfly:11.0.0.Final-alpine
RUN echo "JAVA_OPTS=\"\$JAVA_OPTS -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \"" >> ${JBOSS_HOME}/bin/standalone.conf
EXPOSE 5005
COPY ./build/libs/*.war ./target/*.ear ${JBOSS_HOME}/standalone/deployments/
```
