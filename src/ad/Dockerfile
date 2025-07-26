FROM eclipse-temurin:21-jdk as builder

WORKDIR /usr/src/app

COPY . .

RUN chmod +x ./gradlew

COPY ./pb ./proto

RUN ./gradlew installDist -PprotoSourceDir=./proto

FROM eclipse-temurin:21-jre as release
WORKDIR /usr/src/app
COPY --from=builder /usr/src/app .
ENV AD_PORT 8080
ENTRYPOINT ["./build/install/opentelemetry-demo-ad/bin/Ad"]
