## CMD
- We can define default command in CMD which can be executed at the container run time
- Default command can be replaced when container run

For example:

Dockerfile
------
FROM ubuntu:24.04
CMD ["echo", "Hello Docker"]

suppose we have created a image from using above Dockerfile

when we run the following command it will create an image with the `cmd-demo`
- docker build -t cmd-demo .

then if we run the following command 
- docker run cmd-demo
it will print 'Hello Docker'

if we run the following command
- docker run cmd-demo echo "Hello Mahadi"

Docker will replaced CMD ["echo", "Hello Docker"] with echo "Hello Mahadi"

Therefore CMD = Default command that can be replaced.

## ENTRYPOING

Dockerfile
------
FROM ubuntu:24.04
ENTRYPOINT ["echo", "Hello"]

suppose we have created a image from using above Dockerfile

when we run the following command it will create an image with the `entrypoint-demo`
- docker build -t entrypoint-demo .

then if we run the following command 
- docker run entrypoint-demo
it will print 'Hello'

if we run the following command
- docker run entrypoint-demo Mahadi

it will print the 'Hello Mahadi', that is the command will be appended
ENTRYPOINT = Fixed executable + additional arguments.


Java Spring Boot application
-----------------------------
For a Spring Boot microservice running in Docker:
FROM eclipse-temurin:21-jre

COPY app.jar /app.jar

ENTRYPOINT ["java", "-jar", "/app.jar"]

CMD ["--spring.profiles.active=prod"]
