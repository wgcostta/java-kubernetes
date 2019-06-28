# Java and Kubernetes

Show how you can move your spring boot application to docker and kubernetes

## Part one - base app:

### Requirements:

**Docker and Make**

### Build and run application:

Spring boot and mysql database running on docker

**Build application**
```bash
mvn clean install
```

**Start the database**
```bash
make run:db
```

**Run application**
```bash
java -jar target/java-kubernetes-0.0.1-SNAPSHOT.jar
```

**Check**
http://localhost:8080/persons


## Part two - app on Docker:

Pack application in a docker container

Create a Dockerfile:

```yaml
FROM openjdk:11.0.3-jdk-slim
RUN mkdir /usr/myapp
COPY target/java-kubernetes-0.0.1-SNAPSHOT.jar /usr/myapp/app.jar
WORKDIR /usr/myapp
EXPOSE 8080
CMD ["java", "-Xms128m", "-Xmx256m", "-jar", "app.jar"]
```

Build image
```bash
make build
```

Create and run the container
```bash
make run:app
```

##Good practices

Use enviorement variables

Use entrypoint






