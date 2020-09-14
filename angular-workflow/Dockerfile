FROM node:buster

# Install Netlify CLI for deploy
RUN npm install -g netlify-cli

# Install Angular CLI
RUN npm install -g @angular/cli

RUN apt-get update \
    && apt-get install -y \
      xvfb \
      libxss1 \
      libosmesa6 \
      libgconf-2-4 \
      wget \
 && wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb \
 && (dpkg -i google-chrome-stable_current_amd64.deb; apt-get -fy install; rm google-chrome-stable_current_amd64.deb; apt-get clean; rm -rf /var/lib/apt/lists/* )