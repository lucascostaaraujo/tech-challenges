# Base docker image
FROM python:3.9.18-slim as builder

ARG POETRY_VERSION=1.0.0
ARG POETRY_CORE_VERSION=1.0.0

RUN pip install "poetry==$POETRY_VERSION" \
    && pip install "poetry-core==${POETRY_CORE_VERSION}"