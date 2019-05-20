# spring-boot-installation-example [![Build Status](https://travis-ci.org/daggerok/spring-boot-installation-example.svg?branch=master)](https://travis-ci.org/daggerok/spring-boot-installation-example)
Spring Boot installation on linux. Build executable shell JARs using Gradle / Maven build tools.

## maven

_build_

```bash
./mvnw
```

_test_

```bash
bash target/spring-boot-installation-example-1.0-SNAPSHOT.jar
```

_test in docker_

```bash
docker run --name test --rm -it -p 8080:8080 -v $(pwd)/target:/tmp openjdk:11.0.3-jre-stretch bash
root@8e15c7c2571b:/tmp# bash /tmp/spring-boot-installation-example-1.0-SNAPSHOT.jar
```

_test installation with docker_

```bash
docker run --name test --rm -it -p 8080:8080 -v $(pwd)/target:/tmp openjdk:11.0.3-jre-stretch bash
echo 'JAVA_OPTS="-Dspring.profiles.active=pg-db"' >> /tmp/spring-boot-installation-service.conf
mv /tmp/spring-boot-installation-example-1.0-SNAPSHOT.jar /tmp/spring-boot-installation-service.jar
mkdir -p /etc/init.d/
ln -s /tmp/spring-boot-installation-service.jar /etc/init.d/spring-boot-installation-service
```

## resources

This project was cloned originally from [GitHub: daggerok/spring-fu-jafu-example](https://github.com/daggerok/spring-fu-jafu-example)

NOTE: _This project has been based on [GitHub: daggerok/main-starter](https://github.com/daggerok/main-starter)_
