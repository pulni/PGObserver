FROM ubuntu:latest

RUN apt-get update && apt-get install -y wget

RUN wget -q -O - https://s3.amazonaws.com/influxdb/influxdb_0.9.4.1_amd64.deb > influxdb.deb
RUN dpkg -i influxdb.deb


EXPOSE 8083
EXPOSE 8086
EXPOSE 8088

# change config to disable writing of self-monitoring metrics
RUN sed -i 's/store-enabled = true/store-enabled = false/g' /etc/opt/influxdb/influxdb.conf
RUN mkdir /var/run/influxdb && chmod -R 777 /var/run/influxdb && chmod -R 777 /var/opt/influxdb

ENTRYPOINT ["/opt/influxdb/influxd", "-pidfile", "/var/run/influxdb/influxd.pid", "-config", "/etc/opt/influxdb/influxdb.conf"]
