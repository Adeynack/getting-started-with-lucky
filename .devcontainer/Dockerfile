FROM crystallang/crystal:1.12

SHELL ["/bin/bash", "--login", "-c"]

# Environment
ENV PS1="\[\]\w\$ \[\]"
ENV LANG="C.UTF-8"

# Update/Upgrade
RUN export DEBIAN_FRONTEND=noninteractive && apt update && apt -y upgrade

# Install terminal tools
RUN apt -y install --no-install-recommends tmux curl unzip

# Install PostgreSQL libs & tools
RUN apt -y install --no-install-recommends postgresql-client pspg libpq-dev
ENV PGHOST=127.0.0.1
ENV PGPORT=30402
ENV PGUSER=postgres
ENV PAGER=pspg

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

# Install NodeJS & JS/TS tooling
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash && \
    source ~/.nvm/nvm.sh && \
    nvm install 20 && \
    npm install --global yarn
