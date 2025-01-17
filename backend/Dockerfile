# Stage 1
FROM node:21 AS backend-builder

# Setup working dir
WORKDIR /app

# Code
COPY . .

# Package Install
RUN npm i

# Tests
RUN npm run test

# Stage 2
FROM node:21-slim

WORKDIR /app

# Copy the above stage as compressed
COPY --from=backend-builder /app .

COPY .env.docker .env

# Port
EXPOSE 5000

# App
CMD [ "npm", "start" ]
