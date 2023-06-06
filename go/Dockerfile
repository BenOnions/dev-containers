ARG TAG=1.20-bullseye
FROM golang:${TAG}

# Install build packages
RUN apt update && \
  apt -y install build-essential git ccache cmake make g++-multilib gdb \
  pkg-config coreutils python3-pexpect manpages-dev ninja-build \
  capnproto libcapnp-dev zlib1g-dev && \
  rm -rf /var/lib/apt/lists/*

# Install Mozilla RR debugger and deps
RUN apt update && \
  apt -y install rr

# Install Delve (https://github.com/go-delve/delve)
RUN go install github.com/go-delve/delve/cmd/dlv@latest && \
  go install github.com/cosmtrek/air@latest

# Create project directory (workdir)
WORKDIR /app
