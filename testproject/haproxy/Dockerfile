FROM debian

RUN apt-get -y update && apt-get -y install haproxy
RUN mkdir run/haproxy/

COPY haproxy.cfg /etc/haproxy/haproxy.cfg
COPY script.sh /script.sh
COPY /cert/test.project.com.pem /etc/ssl/certs/test.project.com.pem


ENTRYPOINT ["/script.sh"]
CMD ["haproxy", "-f", "/etc/haproxy/haproxy.cfg"]