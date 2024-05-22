FROM node:16 as build-stage

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build --prod

FROM nginx:apline

COPY nginx.conf /etc/nginx/nginx.conf

COPY --from=build-stage /app/dist/uit-book-network-ui /usr/share/nginx/html

EXPOSE 80