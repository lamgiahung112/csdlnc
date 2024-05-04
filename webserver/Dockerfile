FROM bde2020/hbase-base:1.0.0-hbase1.2.6

COPY project.jar project.jar
COPY openjdk-22.0.1_linux-x64_bin.tar.gz openjdk-22.0.1_linux-x64_bin.tar.gz
COPY /csdlnc-backend /backend
COPY /maven /maven
RUN tar -xvf openjdk-22.0.1_linux-x64_bin.tar.gz

EXPOSE 8080

RUN env JAVA_HOME=/jdk-22.0.1 /maven/bin/mvn clean --f /backend/pom.xml
RUN env JAVA_HOME=/jdk-22.0.1 /maven/bin/mvn install --f /backend/pom.xml -DskipTests
CMD ["env JAVA_HOME=/jdk-22.0.1 /maven/bin/mvn", "spring-boot:run", "--f /backend/pom.xml"]