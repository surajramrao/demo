FROM node:24-alpine

WORKDIR /app

COPY package*.json ./

RUN npm ci --only=production

COPY . .

# Create non-root user & group, give them ownership of /app
RUN addgroup -S student && adduser -S yash -G student \
    && chown -R yash:student /app

# Switch to the non-root user
USER yash

EXPOSE 3000

CMD ["node", "server.js"]
