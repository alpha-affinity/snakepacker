# this Dockerfile demonstrates the creation of an empty venv in the runtime image
ARG PYTHON_MINOR_VERSION

FROM ghcr.io/alpha-affinity/snakepacker/buildtime:master as builder

ARG PYTHON_MINOR_VERSION

RUN python3.${PYTHON_MINOR_VERSION} -m venv ${VIRTUAL_ENV} && \
    pip install -U pip setuptools wheel


FROM ghcr.io/alpha-affinity/snakepacker/runtime:3.${PYTHON_MINOR_VERSION}-master

COPY --from=builder ${VIRTUAL_ENV} ${VIRTUAL_ENV}
