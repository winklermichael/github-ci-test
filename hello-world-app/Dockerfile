# Stage 1: Build the Angular application
FROM node:19.4-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build -- --prod

FROM cgr.dev/chainguard/nginx
COPY --from=builder /app/dist/hello-world-app /usr/share/nginx/html
EXPOSE 80/tcp