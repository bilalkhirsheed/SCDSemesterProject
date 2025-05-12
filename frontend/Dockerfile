FROM node:18 as builder
WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
EXPOSE 3000
RUN npm run build

FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
