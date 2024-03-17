# Use NanoServer as the base image
FROM mcr.microsoft.com/windows/nanoserver:1809 AS backend-builder

# Set working directory inside the container
WORKDIR /app/backend

# Copy package.json and package-lock.json
COPY backend/package*.json ./

# Install Node.js and npm
RUN powershell -Command \
    $url = 'https://nodejs.org/dist/v14.18.3/node-v14.18.3-x64.msi'; \
    $path = 'C:\nodejs.msi'; \
    Invoke-WebRequest -Uri $url -OutFile $path; \
    Start-Process msiexec -ArgumentList '/i', $path, '/quiet', '/norestart' -NoNewWindow -Wait; \
    Remove-Item $path -Force

# Install backend dependencies
RUN npm install

# Copy the rest of the backend application code
COPY backend/ .

# Expose the port your backend app runs on
EXPOSE 3001

# Command to run your backend application
CMD ["node", "server.js"]
