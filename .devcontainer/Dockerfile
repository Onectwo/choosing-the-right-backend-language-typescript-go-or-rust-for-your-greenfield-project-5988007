ARG VARIANT="1.23-bullseye"
FROM mcr.microsoft.com/vscode/devcontainers/go:1-${VARIANT}

# [Choice] Node.js version: none, lts/*, 16, 14, 12, 10
ARG NODE_VERSION="none"
RUN if [ "${NODE_VERSION}" != "none" ]; then su vscode -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi


RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
  && apt-get -y install --no-install-recommends \
  build-essential \
  curl \
  unzip
USER vscode
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs > rustup.sh  \
    && chmod +x rustup.sh \
    && sh rustup.sh -y \
    && rm rustup.sh

RUN curl -fsSL https://bun.sh/install | bash 

# [Optional] Uncomment the next lines to use go get to install anything else you need
# USER vscode
# RUN go get -x <your-dependency-or-tool>

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1
