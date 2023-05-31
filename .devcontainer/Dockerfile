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

WORKDIR /workshop
