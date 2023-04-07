FROM ubuntu:20.04

# Install necessary packages
RUN apt-get update && \
    apt-get install -y curl git make && \
    curl -sL https://deb.nodesource.com/setup_18.x | bash - && \
    apt-get install -y nodejs && \
    curl -sSf https://dl.google.com/go/go1.16.3.linux-amd64.tar.gz | tar -C /usr/local -xz && \
    export PATH=$PATH:/usr/local/go/bin && \
    curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list && \
    # apt-get update && apt-get install -y yarn
    npm install -g yarn

# Set environment variables
ENV PATH="/usr/local/go/bin:${PATH}"

# Verify installation
RUN go version && make --version && yarn --version

# Set working directory
WORKDIR /app

# Copy from the folder above this one to the container
COPY ../. .
# COPY ../ .

# Build application
RUN ls -l
RUN pwd
RUN yarn install --immutable

# Run application
# CMD ["./app"]