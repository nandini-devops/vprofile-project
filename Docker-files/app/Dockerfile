FROM openjdk:11 as BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/nandini-devops/vprofile-project.git
RUN cd vprofile-project && git checkout docker
RUN mvn install
#echo "installation in progress..."
FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/* 
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
#echo "copying artifcats to tomcat root folder..."
EXPOSE 8080
CMD ["catalina.sh","run"]
