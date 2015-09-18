FROM ubuntu:latest

# http://grafana.org/download/builds.html
#ENV GRAFANA_PKG=grafana-latest.linux-x64.tar.gz
ENV GRAFANA_PKG=grafana-2.1.3.linux-x64.tar.gz

ENV GRAFANA_URL=https://grafanarel.s3.amazonaws.com/builds/${GRAFANA_PKG}

RUN apt-get update && apt-get install -y wget
RUN wget -q ${GRAFANA_URL}

RUN mkdir grafana && tar xf ${GRAFANA_PKG} -C grafana --strip-components 1

COPY launch_wrapper.py .

EXPOSE 3000

ENTRYPOINT ["python3", "launch_wrapper.py"]
