# react-frontend/Dockerfile

# ---- Build stage ------------------------------------------------------------
    FROM node:20-alpine AS build
    WORKDIR /app
    
    # Copy lockfiles first for better caching
    COPY package*.json ./
    
    # Install ALL deps, including dev (typescript, vite, etc.)
    RUN npm ci --include=dev
    
    # Copy source and build
    COPY . .
    RUN npm run build
    
    # ---- Runtime stage (Nginx) --------------------------------------------------
    FROM nginx:stable-alpine
    
    # Install curl for healthcheck
    RUN apk add --no-cache curl
    
    # SPA + API proxy config
    COPY nginx.conf /etc/nginx/conf.d/default.conf
    
    # Serve the built assets
    COPY --from=build /app/dist /usr/share/nginx/html
    
    EXPOSE 80
    
    # Healthcheck using curl
    HEALTHCHECK CMD curl -fsS http://localhost/ >/dev/null || exit 1
    