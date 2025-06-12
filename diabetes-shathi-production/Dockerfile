FROM node:18-alpine

WORKDIR /app

# Copy package files
COPY package*.json ./

# Install all dependencies (including dev dependencies needed for build)
RUN npm ci

# Copy all source files
COPY . .

# Build frontend + backend bundles
RUN npm run build

# Remove dev dependencies to keep image small (optional)
RUN npm prune --production

# Expose port 5000
EXPOSE 5000

# Set environment to production
ENV NODE_ENV=production

# Start the app
CMD ["npm", "start"]
