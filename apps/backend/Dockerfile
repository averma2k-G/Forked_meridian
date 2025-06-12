# Step 1: Use Node base image and install pnpm
FROM node:18-alpine

# Install pnpm globally
RUN npm install -g pnpm

# Set working directory
WORKDIR /app

# Copy monorepo root files
COPY pnpm-workspace.yaml ./
COPY package.json pnpm-lock.yaml* ./

# Install all dependencies across workspace
RUN pnpm install --frozen-lockfile

# Copy the entire monorepo code
COPY . .

# Build the backend package
WORKDIR /app/apps/backend
RUN pnpm build

# Expose app port
EXPOSE 8000

# Start the backend (adjust as per your start script if needed)
CMD ["pnpm", "start"]
