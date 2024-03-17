# Use the official Windows NanoServer image as base
FROM mcr.microsoft.com/windows/nanoserver:1709

# Copy the Node.js installer and the PowerShell script to the container
COPY node-v14.19.0-x64.msi C:/
COPY install-node.ps1 C:/

# Run the PowerShell script to install Node.js
RUN powershell -ExecutionPolicy Bypass -File C:\install-node.ps1

# Set the working directory inside the container
WORKDIR C:\app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application
COPY . .

# Expose the port your app runs on
EXPOSE 5000

# Command to run the application
CMD ["node", "server.js"]
