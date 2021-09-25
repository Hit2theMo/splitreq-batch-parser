FROM python:3.8-alpine

ENV CELERY_BROKER_URL redis://redis:6379/0
ENV CELERY_RESULT_BACKEND redis://redis:6379/0

# copy source code
COPY . /worker
WORKDIR /worker

# install requirements
RUN pip install -r requirements.txt
RUN python -m spacy download en_core_web_md


ENTRYPOINT celery -A batch_parsing worker --loglevel=info
