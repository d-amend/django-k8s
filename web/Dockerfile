FROM python:3.9.10-slim

COPY . /app
WORKDIR /app


RUN python3 -m venv /opt/venv

RUN 
    /opt/venv/bin/pip install pip --upgrade && \
    /opt/venv/bin/pip install -r requirements.txt && \
    chmod +x entrypoint.sh

# add this commands, if there are problems with the psycopg binary and you have to build it in the docker container
# apt-get update && \
# apt-get -y install libpq-dev gcc && \
CMD ["/app/entrypoint.sh"]
