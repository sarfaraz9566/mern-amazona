# Use the official Microsoft Windows NanoServer image as base
FROM mcr.microsoft.com/windows/nanoserver:1709

# Install Chocolatey package manager
RUN powershell -Command \
    Set-ExecutionPolicy Bypass -Scope Process -Force; \
    [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; \
    iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

# Install Node.js version 14 using Chocolatey
RUN choco install nodejs-lts -y

# Verify Node.js and npm versions
RUN node -v
RUN npm -v

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
