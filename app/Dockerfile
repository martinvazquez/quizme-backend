# pull official base image
FROM python:3.8-alpine

ARG UNAME=tito
ARG UID=1000
ARG GID=1000

# set work directory
WORKDIR /usr/src/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# for install mysql client
# RUN apk update \
#     && apk add --virtual build-deps gcc python3-dev musl-dev \
#     && apk add --no-cache mariadb-dev

# install dependencies
RUN pip install --upgrade pip
COPY ./requirements.txt .
RUN pip install -r requirements.txt

# copy project
COPY . .

RUN addgroup -g ${GID} -S ${UNAME} && \
    adduser -u ${UID} -S ${UNAME} -G ${UNAME}

USER $UNAME
