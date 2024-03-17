# Use NanoServer as the base image
FROM mcr.microsoft.com/windows/nanoserver:1809 AS frontend-builder

# Set working directory inside the container
WORKDIR /app/frontend

# Copy package.json and package-lock.json
COPY frontend/package*.json ./

# Install Node.js and npm
RUN powershell -Command \
    $url = 'https://nodejs.org/dist/v14.18.3/node-v14.18.3-x64.msi'; \
    $path = 'C:\nodejs.msi'; \
    Invoke-WebRequest -Uri $url -OutFile $path; \
    Start-Process msiexec -ArgumentList '/i', $path, '/quiet', '/norestart' -NoNewWindow -Wait; \
    Remove-Item $path -Force

# Install frontend dependencies
RUN npm install

# Copy the rest of the frontend application code
COPY frontend/ .

# Expose the port your frontend app runs on
EXPOSE 3000

# Command to run your frontend application
CMD ["npm", "start"]
