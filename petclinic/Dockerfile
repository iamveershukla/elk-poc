FROM java:8-jre-alpine
VOLUME /var/log/petclinic
ADD spring-petclinic*.jar spring-petclinic-app.jar
EXPOSE 8085
ENTRYPOINT ["sh", "-c", "java -jar spring-petclinic-app.jar"]
