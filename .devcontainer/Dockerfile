FROM mcr.microsoft.com/devcontainers/base:1-debian

# Install Java 17 (Microsoft) and build essentials
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        curl \
        ca-certificates \
        gnupg \
        coreutils \
        python3-pip \
        python3-venv \
    && mkdir -p /etc/apt/keyrings \
    && curl -sLS https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > /etc/apt/keyrings/microsoft.gpg \
    && echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/microsoft.gpg] https://packages.microsoft.com/debian/12/prod bookworm main" > /etc/apt/sources.list.d/microsoft.list \
    && apt-get update \
    && apt-get -y install msopenjdk-17 \
    && apt-get clean -y && rm -rf /var/lib/apt/lists/*

# Install Poetry using the official installer script
# This installs it to /usr/local so it's accessible to all users
RUN curl -sSL https://install.python-poetry.org | POETRY_HOME=/usr/local python3 -