FROM ubuntu

RUN apt-get update
RUN apt-get clean
RUN apt-get update --allow-releaseinfo-change
RUN apt-get install flask
COPY app.py /opt/app.py

ENTRYPOINT FLASK_APP=/opt/app.py flask tun --host=0.0.0.0

