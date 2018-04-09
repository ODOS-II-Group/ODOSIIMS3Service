FROM docker.lassiterdynamics.com:5000/centos7-java8

# Download and Install newrelic java agent
ADD https://s3.amazonaws.com/tics2/newrelic-java-3.48.0.zip /tmp/newrelicclient.zip
RUN unzip /tmp/newrelicclient.zip -d /tmp/

# Copy application specified newrelic yml file
COPY newrelic.yml /tmp/newrelic

ENV SPRING_OUTPUT_ANSI_ENABLED=ALWAYS \
    JHIPSTER_SLEEP=0 \
    JAVA_OPTS="-javaagent:/tmp/newrelic/newrelic.jar"

CMD echo "The application will start in ${JHIPSTER_SLEEP}s..." && \
    sleep ${JHIPSTER_SLEEP} && \
    java ${JAVA_OPTS} -Djava.security.egd=file:/dev/./urandom -jar /app.war

EXPOSE 8083 5701/udp

ADD *.war /app.war

USER centos
