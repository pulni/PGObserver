FROM ubuntu:latest

RUN apt-get update && apt-get install -y git

RUN git clone git@github.com:zalando/PGObserver.git

WORKDIR PGObserver/extra_features/influxdb_adapter

ENTRYPOINT ["python2", "export_to_influxdb.py", "-v"]
