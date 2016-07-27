FROM ubuntu:16.04

# Update aptitude with new repo
RUN apt-get update

RUN apt-get -y install curl git

RUN cd /tmp && curl -sL https://deb.nodesource.com/setup_6.x | bash -

RUN apt-get install -y nodejs

RUN npm install -g bower nodemon



ENV DEBUG=UrbIS
ENV PORT=3003
ENV NODE_PATH=/var/local/urbisnode/node_modules:$NODE_PATH
