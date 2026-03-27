# this Dockerfile has just enough python to run your venv
ARG BASE_IMAGE
ARG BASE_TAG
FROM ${BASE_IMAGE}:${BASE_TAG}

ARG PYTHON_MINOR_VERSION
ARG PYTHON_DISTUTILS
RUN apt-install \
        python3.${PYTHON_MINOR_VERSION}${PYTHON_DISTUTILS} \
        # python >= 3.12 has no -minimal package:
        # see: https://github.com/deadsnakes/py3.12/commit/675bbcb47d1ed04cf6fa59c1659281769fa7a676#diff-0a1054b190b852d0fffe209f18d7af7010dc7fd4ef76e440afaf0a8d6e7f1fa2
        && if [ "${PYTHON_MINOR_VERSION}" -lt 12 ]; then \
            apt-install python3.${PYTHON_MINOR_VERSION}-minimal; \
        fi \
        && apt-install libpython3.${PYTHON_MINOR_VERSION}-stdlib
