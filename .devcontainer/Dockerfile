ARG VARIANT="16-buster"
FROM mcr.microsoft.com/vscode/devcontainers/javascript-node:${VARIANT}

RUN wget -q -O - https://packages.cloudfoundry.org/debian/cli.cloudfoundry.org.key | apt-key add - ; \
echo "deb https://packages.cloudfoundry.org/debian stable main" | tee /etc/apt/sources.list.d/cloudfoundry-cli.list

RUN apt-get update \
&& apt-get -y install --no-install-recommends cf7-cli sqlite3 libsqlite3-dev

RUN su node -c "npm install -g @ui5/cli @sap/cds-dk yo"

## Install BTP Cli
RUN bash -c "echo -ne '\n' | bash <(curl -L https://raw.githubusercontent.com/SAP-samples/sap-tech-bytes/2021-09-01-btp-cli/getbtpcli)"

## Add BTP to Path
ENV PATH "$PATH:./root/bin/"
