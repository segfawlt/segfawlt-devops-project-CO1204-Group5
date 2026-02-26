# Stage 1: builder – install all deps and copy source
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .

# Stage 2: production – lean image with only prod deps
FROM node:18-alpine AS production
WORKDIR /app
COPY package*.json ./
RUN npm install --only=production
COPY --from=builder /app/server.js ./
EXPOSE 8080
CMD ["node", "server.js"]
