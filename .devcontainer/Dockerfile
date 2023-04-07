FROM ubuntu:20.04

# Commands to include:
# Install required utils
RUN apt-get update && apt-get install -y wget make curl

# Install Go
WORKDIR /tmp/goinstall
RUN wget https://go.dev/dl/go1.20.3.linux-amd64.tar.gz
RUN tar -xvf go1.20.3.linux-amd64.tar.gz 
# RUN rm -R /usr/local/go
RUN mv go /usr/local
RUN echo "export GOROOT=/usr/local/go" >> ~/.bashrc
RUN echo "export GOPATH=$HOME/go" >> ~/.bashrc
RUN echo "export PATH=$GOPATH/bin:$GOROOT/bin:$PATH" >> ~/.bashrc

# Install node
RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | bash &&\
apt-get install -y nodejs


# Install yarn
RUN npm install -g yarn



# Set environment variables
ENV PATH="/usr/local/go/bin:${PATH}"

# Verify installation
# RUN go version && make --version && yarn --version

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


# # Latest commands from history: 
# sudo -E "PATH=$PATH" /home/ubuntu/.nvm/versions/node/v18.15.0/lib/node_modules/yarn/bin/yarn.js start
# make run
