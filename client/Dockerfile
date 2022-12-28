FROM node:18-alpine AS build
WORKDIR /app
COPY ./package.json ./
RUN npm i
COPY . .
RUN npm run build
# PHASE 2) Deploy using NGNIX
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=build /app/build /usr/share/nginx/html