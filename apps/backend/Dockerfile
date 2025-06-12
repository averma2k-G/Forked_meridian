# Use a lightweight Node.js image
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Copy package files and install dependencies
COPY apps/backend/package*.json ./
RUN npm install --production

# Copy source code
COPY apps/backend/src ./src

# If you have a build step (like tsc), add it here:
# RUN npm run build

# Expose the port your app listens on
EXPOSE 8000

# Start the app (update if your start script differs)
CMD ["npm", "start"]
