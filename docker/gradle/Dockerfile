# gradle build
# docker build --no-cache -t gradle -f docker/gradle/Dockerfile .
# docker run --rm -it -p 80:8080 --name gradle-app gradle
# docker run -d --rm -p 80:8080 --name gradle-app gradle
FROM openjdk:11.0.3-jre-stretch
ENTRYPOINT mkdir -p /etc/init.d /var/log/ \
 && touch /tmp/app.jar /var/log/app.log \
 && ln -s /tmp/app.jar /etc/init.d/app \
 && echo 'JAVA_OPTS="-Dspring.profiles.active=gradle,production -Ddebug=false"\
' > /tmp/app.conf \
 && service app start \
 && tail -f /var/log/app.log
CMD /bin/bash
EXPOSE 8080
HEALTHCHECK --timeout=2s \
            --retries=22 \
            CMD curl -f http://127.0.0.1:8080/ || exit 1
COPY build/libs/*-SNAPSHOT.jar /tmp/app.jar
