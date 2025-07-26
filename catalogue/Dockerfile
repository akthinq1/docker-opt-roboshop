FROM alpine:3.21
WORKDIR /opt/server
COPY *.js .
COPY package.json .
RUN npm install
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["nod", "server.js"]