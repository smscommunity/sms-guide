FROM mcr.microsoft.com/vscode/devcontainers/ruby:2

ENV LANG=en_US.UTF-8 \
  LANGUAGE=en_US:en \
  TZ=Etc/UTC \
  LC_ALL=en_US.UTF-8 \
  LANG=en_US.UTF-8 \
  LANGUAGE=en_US

RUN gem install bundler

ARG NODE_VERSION="lts/*"
RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"
