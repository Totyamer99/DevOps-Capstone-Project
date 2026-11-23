FROM node:24-alpine AS builder
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci --omit=dev
FROM node:24-alpine AS runtime
WORKDIR /app
COPY --from=builder /app/node_modules ./node_modules
COPY package.json package-lock.json ./
COPY src ./src
USER root
EXPOSE 3000
CMD ["node", "src/server.js"]
