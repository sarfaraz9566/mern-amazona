# Use the official Windows NanoServer image as base
FROM mcr.microsoft.com/windows/nanoserver

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install --quiet

# Copy the rest of the application
COPY . .

# Expose the port your app runs on
EXPOSE 5000

# Command to run the application
CMD ["node", "server.js"]
