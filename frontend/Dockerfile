# Use the official Microsoft Windows NanoServer image as base
FROM mcr.microsoft.com/windows/nanoserver:1709

# Download the Node.js installer for Windows (64-bit)
ADD https://nodejs.org/dist/v14.19.0/node-v14.19.0-x64.msi nodejs_installer.msi

# Install Node.js using PowerShell
RUN powershell -Command Start-Process -FilePath 'C:\nodejs_installer.msi' -ArgumentList '/quiet', '/qn', '/norestart' -Wait

# Set the working directory inside the container
WORKDIR C:\app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install 

# Copy the rest of the application
COPY . .

# Build the React app
RUN npm run build

# Expose the port your app runs on
EXPOSE 3000

# Command to run the application
CMD ["npm", "start"]
