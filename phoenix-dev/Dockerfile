FROM midas/elixir-dev:1.0.4

MAINTAINER C. Jason Harrelson "jason@lookforwardenterprises.com"

# Fetch phoenix installer version 0.13.1
RUN mix archive.install https://github.com/phoenixframework/phoenix/releases/download/v0.13.1/phoenix_new-0.13.1.ez --force

# Download and Install npm
RUN gpg --keyserver pool.sks-keyservers.net --recv-keys 7937DFD2AB06298B2293C3187D33FF9D0246406D 114F43EE0176B71C7BC219DD50A3051F888C628D

ENV NODE_VERSION 0.12.2
ENV NPM_VERSION 2.7.3

RUN curl -SLO "http://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION-linux-x64.tar.gz" \
 && curl -SLO "http://nodejs.org/dist/v$NODE_VERSION/SHASUMS256.txt.asc" \
 && gpg --verify SHASUMS256.txt.asc \
 && grep " node-v$NODE_VERSION-linux-x64.tar.gz\$" SHASUMS256.txt.asc | sha256sum -c - \
 && tar -xzf "node-v$NODE_VERSION-linux-x64.tar.gz" -C /usr/local --strip-components=1 \
 && rm "node-v$NODE_VERSION-linux-x64.tar.gz" SHASUMS256.txt.asc \
 && npm install -g npm@"$NPM_VERSION" \
 && npm cache clear
