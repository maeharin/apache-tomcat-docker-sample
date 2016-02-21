FROM tomcat:7-jre8

ADD tomcat-users.xml /usr/local/tomcat/conf/

RUN rm -rf /usr/local/tomcat/webapps/ROOT

CMD ["catalina.sh", "run"]
