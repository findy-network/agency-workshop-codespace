FROM mcr.microsoft.com/devcontainers/java:0-17

ENV PATH=$PATH:/usr/local/go/bin
ENV GOVERSION=1.20.4
ENV GO_TOOLS="\
  github.com/cweill/gotests/gotests@latest \
  github.com/fatih/gomodifytags@latest \
  github.com/josharian/impl@latest \
  github.com/haya14busa/goplay/cmd/goplay@latest \
  github.com/go-delve/delve/cmd/dlv@latest \
  honnef.co/go/tools/cmd/staticcheck@latest \
  golang.org/x/tools/gopls@latest"

RUN ARCH=$(dpkg --print-architecture) && \
  #### install Go ####
  curl -O -L "https://golang.org/dl/go${GOVERSION}.linux-${ARCH}.tar.gz" && \
  tar -C /usr/local -xzf go${GOVERSION}.linux-${ARCH}.tar.gz && \
  rm go${GOVERSION}.linux-${ARCH}.tar.gz && \
  echo "${GO_TOOLS}" | xargs -n 1 go install -v && \
  #### install findy-agent-cli ####
  curl https://raw.githubusercontent.com/findy-network/findy-agent-cli/HEAD/install.sh >install.sh && \
  chmod a+x install.sh && \
  sudo ./install.sh -b /bin && \
  rm ./install.sh

#### install Gradle ####
ENV GRADLE_VERSION=8.1.1
RUN cd /usr/local && \
  curl -L https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip -o gradle-${GRADLE_VERSION}-bin.zip && \
  unzip gradle-${GRADLE_VERSION}-bin.zip && \
  rm gradle-${GRADLE_VERSION}-bin.zip

ENV GRADLE_HOME=/usr/local/gradle-${GRADLE_VERSION}
ENV PATH=$PATH:$GRADLE_HOME/bin
ENV JAVA_HOME=/usr/lib/jvm/msopenjdk-current

USER vscode

#### install NVM ####
ENV NVM_DIR=/home/vscode/.nvm
RUN curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash && \
  . $NVM_DIR/nvm.sh && \
  #### clone workshop codes and install deps ####
  git clone https://github.com/findy-network/agency-workshop.git /home/vscode/workshop && \
  cd /home/vscode/workshop/track2.1-ts/app && nvm install && npm install && \
  cd /home/vscode/workshop/track2.2-go/app && go mod tidy && \
  cd /home/vscode/workshop/track2.3-kt/app && gradle build


WORKDIR /home/vscode/workshop