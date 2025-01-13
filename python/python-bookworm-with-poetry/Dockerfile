ARG PYTHON_VERSION=3.12
FROM python:${PYTHON_VERSION}
ARG POETRY_VERSION=1.8.3
ARG POETRY_PLUGIN_PYPI_MIRROR_VERSION=0.4.3

WORKDIR /app

# install poetry
ENV POETRY_HOME=/opt/poetry
ENV PATH="${POETRY_HOME}/bin:${PATH}"
RUN python3 -m venv $POETRY_HOME && $POETRY_HOME/bin/pip install poetry==${POETRY_VERSION} && $POETRY_HOME/bin/poetry --version
RUN poetry --version

# 加速镜像
RUN poetry self add poetry-plugin-pypi-mirror@${POETRY_PLUGIN_PYPI_MIRROR_VERSION}
ENV POETRY_PYPI_MIRROR_URL=https://mirrors.cloud.tencent.com/pypi/simple

