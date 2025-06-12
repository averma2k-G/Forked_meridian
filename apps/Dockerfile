# Use official Node.js LTS image
FROM node:18-slim

# Set working directory inside container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json (or yarn.lock)
COPY apps/backend/package*.json ./

# Install dependencies
RUN npm install --production

# Copy source code
COPY apps/backend/src ./src
COPY apps/backend/tsconfig.json ./

# Build TypeScript
RUN npx tsc

# Expose backend port (update if different)
EXPOSE 8000

# Start the backend app - adjust if your start script is different
CMD ["node", "dist/index.js"]
