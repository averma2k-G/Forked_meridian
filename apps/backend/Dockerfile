FROM node:18-alpine

# Install pnpm globally
RUN npm install -g pnpm

WORKDIR /app

# Copy only root package files first (assumes monorepo structure)
COPY pnpm-workspace.yaml ./
COPY package.json pnpm-lock.yaml* ./

# Install dependencies (recursively across workspace)
RUN pnpm install --frozen-lockfile

# Copy the full monorepo (including backend and shared packages)
COPY . .

# Build the backend package
WORKDIR /app/apps/backend
RUN pnpm build

EXPOSE 8000

CMD ["node", "dist/index.js"]
