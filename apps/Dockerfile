FROM node:18-alpine

RUN npm install -g pnpm

WORKDIR /app

# Copy all files (workspace root, all packages, lockfile)
COPY . .

# Install all dependencies in the workspace
RUN pnpm install --frozen-lockfile

# Build backend from root context (runs tsc in apps/backend)
RUN pnpm --filter @meridian/backend run build

# Expose backend port
EXPOSE 8000

# Run backend start script from root context
CMD ["pnpm", "--filter", "@meridian/backend", "start"]
