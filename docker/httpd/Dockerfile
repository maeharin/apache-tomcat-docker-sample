FROM centos:7

RUN yum -y update && yum clean all
RUN yum -y install httpd httpd-devel gcc* make && yum clean all

# Install mod_jk
RUN curl -SL http://mirror.sdunix.com/apache/tomcat/tomcat-connectors/jk/tomcat-connectors-1.2.40-src.tar.gz -o tomcat-connectors-1.2.40-src.tar.gz \
    && mkdir -p src/tomcat-connectors \
    && tar xzf tomcat-connectors-1.2.40-src.tar.gz -C src/tomcat-connectors --strip-components=1 \
    && cd src/tomcat-connectors/native/ \
    && ./configure --with-apxs=/usr/bin/apxs \
    && make \
    && cp apache-2.0/mod_jk.so /usr/lib64/httpd/modules/ \
    && ./libtool --finish /usr/lib64/httpd/modules/ \
    && cd / \
    && rm -rf src/ \
    && rm -f tomcat-connectors-1.2.40-src.tar.gz


# mod_jk conf files
ADD mod_jk.conf /etc/httpd/conf.d/
ADD workers.properties /etc/httpd/conf.d/

EXPOSE 80

# Simple startup script to avoid some issues observed with container restart 
ADD run-httpd.sh /run-httpd.sh
RUN chmod -v +x /run-httpd.sh

CMD ["/run-httpd.sh"]
