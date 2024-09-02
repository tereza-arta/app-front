FROM node:14-alpine as builder

WORKDIR /app

# add '/app/node_modules/.bin' to $PATH
ENV PATH /app/node_modules/.bin:$PATH
# install application dependencies
COPY package*.json ./
RUN npm install
# RUN npm install react-scripts -g

# copy app files
COPY . .

CMD ["npm", "start"]

FROM nginx:alpine
COPY ./.nginx/nginx.conf /etc/nginx/nginx.conf

## Remove default nginx index pagec
RUN rm -rf /usr/share/nginx/html/*

# Copy from the stage 1
COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 3000
ENTRYPOINT ["nginx", "-g", "daemon off;"]
