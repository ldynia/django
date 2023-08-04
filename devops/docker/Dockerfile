ARG PY_DIST=alpine \
    PY_VER=3.11
FROM python:${PY_VER}-${PY_DIST}

ARG GROUP=nogroup \
    PORT=8000 \
    PY_VER=3.11 \
    USER=nobody \
    WORKDIR=/usr/src

ENV PORT=$PORT \
    PYTHONIOENCODING=UTF-8 \
    PYTHONUNBUFFERED=True

WORKDIR ${WORKDIR}
COPY . ${WORKDIR}

RUN apk add \
    curl \
    gcc \
    libpq \
    musl-dev \
    postgresql-dev

RUN chown -R ${USER}:${GROUP} \
    /usr/local/bin \
    /usr/local/lib/python${PY_VER} \
    ${WORKDIR}

EXPOSE ${PORT}
VOLUME ${WORKDIR}

USER ${USER}:${GROUP}

HEALTHCHECK CMD curl -f http://localhost:${PORT}/ || exit 1

ENTRYPOINT ["/usr/src/scripts/startup.sh"]
#ENTRYPOINT ["/usr/src/scripts/startup.sh", "sleep", "1d"]
