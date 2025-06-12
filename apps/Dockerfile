# Use official Node.js LTS image with pnpm
FROM node:18-alpine

# Install pnpm globally
RUN npm install -g pnpm

# Set working directory
WORKDIR /app

# Copy all files first (including pnpm-workspace.yaml and all package.jsons)
COPY . .

# Install all dependencies in monorepo
RUN pnpm install --frozen-lockfile

# Build backend (adjust if backend build is different)
WORKDIR /app/apps/backend
RUN pnpm build

# Expose backend port
EXPOSE 8000

# Start backend app
CMD ["pnpm", "start"]
