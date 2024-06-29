FROM crystallang/crystal:1.12
# FROM ubuntu:24.04 # if uncommented, uncomment also section "Install Crystal"

SHELL ["/bin/bash", "--login", "-c"]

# Environment
ENV PS1="\[\]\w\$ \[\]"
ENV LANG="C.UTF-8"

# Update/Upgrade
RUN export DEBIAN_FRONTEND=noninteractive && apt update && apt -y upgrade

# Install terminal tools
RUN apt -y install --no-install-recommends tmux curl unzip

# Install PostgreSQL libs & tools
RUN apt -y install --no-install-recommends postgresql-client pspg libpq-dev git ca-certificates gpg
ENV PGHOST=127.0.0.1
ENV PGPORT=30402
ENV PGUSER=postgres
ENV PAGER=pspg

# Install Crystal (uncomment if switching back to FROM ubuntu:24.04)
# RUN curl -fsSL https://packagecloud.io/84codes/crystal/gpgkey | gpg --dearmor | tee /etc/apt/trusted.gpg.d/84codes_crystal.gpg > /dev/null && \
#     echo "deb https://packagecloud.io/84codes/crystal/any any main" | tee /etc/apt/sources.list.d/84codes_crystal.list && \
#     apt update && \
#     apt install -y crystal && \
#     which crystal

# Install `Lucky` (CLI for the framework)
RUN apt install -y libc6-dev libevent-dev libpcre2-dev libpcre3-dev libpng-dev libssl-dev libyaml-dev zlib1g-dev && \
    git clone https://github.com/luckyframework/lucky_cli && \
    cd lucky_cli && \
    git checkout v1.2.0 && \
    shards install --without-development && \
    shards build --production && \
    cp bin/lucky /usr/local/bin && \
    cd .. && \
    rm -rf lucky_cli && \
    which lucky

# Install NodeJS & JS/TS tooling
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash && \
    source ~/.nvm/nvm.sh && \
    nvm install 20 && \
    npm install --global yarn
