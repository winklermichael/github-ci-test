# Stage 1: Build the Angular application
FROM node:20.12-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build -- --configuration=production

FROM cgr.dev/chainguard/nginx
COPY --from=builder /app/dist/hello-world-app /usr/share/nginx/html
EXPOSE 80/tcp