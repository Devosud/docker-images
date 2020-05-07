FROM node:latest

# Set working directory
RUN mkdir /myapp
WORKDIR /myapp

# Add chromium for karma tests
RUN apt-get update \
    && apt-get install -y chromium

# Install Angular CLI
RUN npm install -g @angular/cli
# Install Netlify CLI for deploy
RUN npm install -g netlify-cli

# Add `/usr/src/app/node_modules/.bin` to $PATH
ENV PATH /myapp/node_modules/.bin:$PATH
ENV CHROME_BIN=/usr/bin/chromium
