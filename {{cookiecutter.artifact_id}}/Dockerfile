FROM  debian:buster-slim

LABEL org.opencontainers.image.title="{{ cookiecutter.artifact_name }}"
LABEL org.opencontainers.image.description="{{ cookiecutter.artifact_description }}"
LABEL org.opencontainers.image.url="https://github.com/{{ cookiecutter.artifact_repo }}"
LABEL org.opencontainers.image.documentation="https://github.com/{{ cookiecutter.artifact_repo }}"
LABEL org.opencontainers.image.source="https://github.com/{{ cookiecutter.artifact_repo }}"
LABEL org.opencontainers.image.revision="v0.0.0"
LABEL org.opencontainers.image.vendor="{{ cookiecutter.artifact_org }}"
LABEL org.opencontainers.image.authors="{{ cookiecutter.artifact_author }}"


# copy package list
COPY pkg.list .

# Install basic tools
RUN apt-get update \
    && apt-get install --yes $(cat pkg.list) \
    && apt-get autoremove \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["tini", "--"]
CMD ["/bin/bash"]