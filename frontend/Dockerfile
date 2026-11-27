
# Stage 1: Build Quasar SPA
FROM node:22-alpine AS builder

WORKDIR /app

COPY package*.json ./
RUN npm ci --legacy-peer-deps --ignore-scripts

COPY . .

RUN npx quasar prepare
RUN npm run build

# Stage 2: Production with Nginx
FROM nginx:1.27-alpine

COPY --from=builder /app/dist/spa /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
