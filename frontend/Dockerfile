FROM node:13.8.0 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM node:13.8.0-slim
WORKDIR /app
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/package*.json ./
RUN npm install
RUN npm audit fix --force --audit-level=critical
RUN npm audit fix --force --audit-level=critical
RUN npm audit fix --force --audit-level=critical
RUN npm audit fix --force --audit-level=critical
RUN npm audit --audit-level=critical || true

EXPOSE 8081
CMD [ "node", "dist/index.js" ]
