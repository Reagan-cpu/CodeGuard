# Use a Debian-based Node.js image for better package compatibility
FROM node:20-bookworm-slim

# Install all required runtimes
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    openjdk-17-jdk \
    build-essential \
    curl \
    bash \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install --omit=dev

# Copy source code
COPY . .

# Set environment variables for Render
ENV NODE_ENV=production \
    PORT=5002 \
    ALLOW_LOCAL_EXECUTION=true

# Expose port
EXPOSE 5002

# Run the server
CMD ["node", "src/server.js"]
