FROM crystallang/crystal:1.12

RUN git clone https://github.com/luckyframework/lucky_cli && \
    cd lucky_cli && \
    git checkout v1.2.0 && \
    shards install --without-development && \
    shards build --production && \
    cp bin/lucky /usr/local/bin && \
    cd .. && \
    rm -rf lucki_cli && \
    which lucky
