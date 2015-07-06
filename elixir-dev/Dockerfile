FROM hqmq/docker-elixir:1.0.4.0

MAINTAINER C. Jason Harrelson "jason@lookforwardenterprises.com"

RUN rm -f /etc/service/sshd/down
RUN /etc/my_init.d/00_regen_ssh_host_keys.sh

RUN apt-get update && apt-get -y install git postgresql-client build-essential autotools-dev automake

# Setting locale as Elixir is choosy about it
RUN locale-gen en_US.UTF-8
ENV LANGUAGE en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8

# Install rebar (Erlang's Mix) and Hex (Elixir's Package Manager)
RUN mix local.rebar \
  && mix local.hex --force

RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
