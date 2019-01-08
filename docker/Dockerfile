FROM openjdk:12-alpine AS build-env

RUN apk add --no-cach git maven

RUN mkdir /bank-java/

WORKDIR /bank-java/
ADD . /bank-java/

RUN mvn clean install -Dmaven.test.skip=true

FROM openjdk:12-alpine

WORKDIR /

COPY --from=build-env /bank-java/target/bank-java.jar /
EXPOSE 8080

CMD java -jar bank-java.jar