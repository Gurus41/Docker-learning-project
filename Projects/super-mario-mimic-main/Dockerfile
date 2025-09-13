# ---------- Dockerfile ----------

# Build stage
FROM node:18-alpine AS build
WORKDIR /app

# copy package files first for caching
COPY package*.json ./

# install dependencies
RUN npm ci

# copy rest of the app and build
COPY . .
RUN npm run build

# Runtime stage (serve static files)
FROM node:18-alpine AS runtime
WORKDIR /app

# copy built assets
COPY --from=build /app/dist ./dist

# install a tiny static http server
RUN npm install -g http-server

EXPOSE 8080
CMD ["http-server", "dist", "-p", "8080", "-c-1"]
