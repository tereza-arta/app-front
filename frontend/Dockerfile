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

#EXPOSE 3000

CMD ["npm", "start"]


FROM nginx:alpine
COPY ./.nginx/nginx.conf /etc/nginx/nginx.conf

## Remove default nginx index pagec
RUN rm -rf /usr/share/nginx/html/*

# Copy from the stage 1
COPY --from=builder /app /usr/share/nginx/html

EXPOSE 80
ENTRYPOINT ["nginx", "-g", "daemon off;"]
