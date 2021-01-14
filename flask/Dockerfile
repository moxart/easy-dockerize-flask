FROM python:3-slim-buster

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN apt-get update -y && \
    pip install --upgrade pip && \
    apt-get install -y --no-install-recommends gcc && \
    apt-get clean && \
    rm -rf /var/cache/apk/*

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 80
CMD gunicorn --bind 0.0.0.0:8000 app:app