# Stage 2: run
FROM lucascostaaraujo/python-poetry:3.9.18-1.0@sha256:002c4d5d0d5c1dc74d6a1898e8b40ee8232ab75657fa5acf852187510c9a060b

ARG APP_NAME
LABEL app=${APP_NAME}

ARG DEPLOYMENT_USER=ironman
ARG WORK_DIR=/usr/app

WORKDIR $WORK_DIR

RUN useradd --system --home  $WORK_DIR $DEPLOYMENT_USER \
    && chown -R $DEPLOYMENT_USER:$DEPLOYMENT_USER $WORK_DIR
ENV PATH /home/${DEPLOYMENT_USER}/.local/bin:${PATH}

COPY --chown=$DEPLOYMENT_USER:$DEPLOYMENT_USER pyproject.toml .
COPY --chown=$DEPLOYMENT_USER:$DEPLOYMENT_USER app.py .

RUN poetry install

USER $DEPLOYMENT_USER


EXPOSE 8000


ENTRYPOINT ["poetry", "run", "uvicorn", "app:app" , "--host", "0.0.0.0", "--port", "8000", "--reload"]