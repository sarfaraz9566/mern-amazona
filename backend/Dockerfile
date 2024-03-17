# Use the official Windows Server Core image as the base image
FROM mcr.microsoft.com/windows/servercore:ltsc2019

# Download the Node.js installer for Windows (64-bit)
ADD https://nodejs.org/dist/v14.19.0/node-v14.19.0-x64.msi nodejs_installer.msi

# Install Node.js using PowerShell
RUN powershell -Command Start-Process -FilePath 'C:\nodejs_installer.msi' -ArgumentList '/quiet', '/qn', '/norestart' -Wait

# Set the working directory inside the container
WORKDIR C:\app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install npm dependencies
RUN npm install

# Copy the rest of the backend application files to the working directory
COPY . .

# Expose port 5000 (adjust as needed)
EXPOSE 5000

# Start the backend server
CMD ["node", "server.js"]
