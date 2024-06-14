FROM crystallang/crystal:1.12

# Update/Upgrade
RUN export DEBIAN_FRONTEND=noninteractive && apt update && apt -y upgrade

# Install PostgreSQL libs & tools
RUN apt -y install --no-install-recommends postgresql-client pspg libpq-dev
ENV PGHOST=127.0.0.1
ENV PGPORT=30002
ENV PGUSER=postgres
ENV PAGER=pspg

# Install terminal tools
RUN apt -y install --no-install-recommends tmux

# Install `Lucky` (CLI for the framework)
RUN git clone https://github.com/luckyframework/lucky_cli && \
    cd lucky_cli && \
    git checkout v1.2.0 && \
    shards install --without-development && \
    shards build --production && \
    cp bin/lucky /usr/local/bin && \
    cd .. && \
    rm -rf lucki_cli && \
    which lucky

# Environment
ENV PS1="\[\]\w\$ \[\]"
