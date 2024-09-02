FROM node:14-alpine as builder

WORKDIR /app

# add '/app/node_modules/.bin' to $PATH
ENV PATH /app/node_modules/.bin:$PATH

# install application dependencies
COPY package*.json ./

pod/web-deployment-f-568bc8cd4c-hcv9h
RUN npm install

# copy app files
COPY . .

EXPOSE 3000

CMD ["npm", "start"]
