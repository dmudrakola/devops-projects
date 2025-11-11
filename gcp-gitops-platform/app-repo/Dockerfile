# Build Stage
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build # if applicable

# Runtime Stage
FROM node:20-slim
WORKDIR /app
COPY --from=builder /app .
EXPOSE 8080
CMD ["node", "server.js"]
