FROM maven:3.9.9-eclipse-temurin-21-jammy AS build
RUN git clone https://github.com/hkhcoder/vprofile-project.git
RUN cd vprofile-project && git checkout containers && mvn clean install


FROM tomcat:10-jdk21
LABEL "Project"="Vprofile"
LABEL "Author"="Nalini"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build vprofile-project/target/vprofile.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh","run"]


