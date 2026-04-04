FROM mcr.microsoft.com/devcontainers/base:1-debian

# Install Java, Poetry, and Core Utils
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        curl \
        ca-certificates \
        gnupg \
        pipx \
        coreutils \
    && mkdir -p /etc/apt/keyrings \
    && curl -sLS https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > /etc/apt/keyrings/microsoft.gpg \
    && chmod go+r /etc/apt/keyrings/microsoft.gpg \
    && echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/microsoft.gpg] https://packages.microsoft.com/debian/12/prod bookworm main" > /etc/apt/sources.list.d/microsoft.list \
    && apt-get update \
    && apt-get -y install msopenjdk-17 \
    && apt-get clean -y && rm -rf /var/lib/apt/lists/*

# Install Poetry
RUN pipx install poetry --include-deps