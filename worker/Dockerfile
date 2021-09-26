FROM python:3.8-buster
#RUN apk add antiword musl-dev linux-headers g++ libxslt-dev
#RUN apt-get -y install antiword 
RUN apt-get update && apt-get install -y antiword

ENV CELERY_BROKER_URL redis://redis:6379/0
ENV CELERY_RESULT_BACKEND redis://redis:6379/0

# copy source code
COPY . /worker
WORKDIR /worker

# install requirements
#RUN pip install --upgrade pip setuptools wheel
RUN pip install -r requirements.txt
RUN python -m spacy download en_core_web_md

ENTRYPOINT celery -A batch_parsing worker --loglevel=info
