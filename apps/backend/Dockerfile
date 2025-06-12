# Use Node.js base image
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Copy package.json and install deps
COPY apps/backend/package*.json ./
RUN npm install

# Copy the rest of the backend code
COPY apps/backend/ ./

# Build the TypeScript code
RUN npm run build

# Expose the port (if used by Cloudflare Workers, may not apply)
EXPOSE 8000

# Start the compiled app
CMD ["node", "dist/index.js"]
