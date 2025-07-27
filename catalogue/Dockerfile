# changed base os from node to alpine node
# create a system user as roboshop or any name and run it as normal user
# search alpine add user and group
# change ownership from sudo to roboshop, if no sudo access just give owne permissions to robosop

# # FROM node:20
# FROM node:20-alpine3.21
# RUN addgroup roboshop -S && adduser -S roboshop -G roboshop
# WORKDIR /opt/server
# RUN chown -R roboshop:roboshop /opt/server
# USER roboshop
# COPY *.js .
# COPY package.json .
# RUN npm install
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node", "server.js"]


# use multistage bulid to optimise code for save more space

# stage one for package installations and cache controll
FROM node:20-alpine3.21 AS builder
WORKDIR /opt/server
COPY *.js .
COPY package.json .
RUN npm install

FROM node:20-alpine3.21
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
WORKDIR /opt/server
USER roboshop
COPY --from=builder /opt/server /opt/server 
CMD ["node", "server.js"]
