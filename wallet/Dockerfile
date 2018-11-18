FROM ubuntu:16.04

RUN set -ex

RUN apt-get update && \
    apt-get --no-install-recommends --yes install ca-certificates wget unzip jq curl && \
    apt-get clean && \
    rm -rf /var/lib/apt

RUN useradd -ms /bin/bash loki

USER loki

WORKDIR /home/loki

RUN wget -O loki.zip `curl -s https://api.github.com/repos/loki-project/loki/releases/latest | jq -r ".assets[] | select(.name | test(\"linux\")) | .browser_download_url"`
RUN unzip loki.zip && rm loki.zip
RUN mv `echo loki-*` lokid

# Contains the blockchain
VOLUME /home/loki/.lokid

EXPOSE 18080
EXPOSE 18081

WORKDIR /home/loki/lokid

ENTRYPOINT ["./lokid", "--p2p-bind-ip=0.0.0.0", "--p2p-bind-port=18080", "--rpc-bind-ip=0.0.0.0", "--rpc-bind-port=18081", "--non-interactive", "--confirm-external-bind"]
