# Use the Windows NanoServer base image
FROM mcr.microsoft.com/windows/nanoserver:1809

# Set environment variables
ENV NODE_VERSION 14.17.1
ENV NPM_VERSION 6.14.13

# Install Node.js and NPM
RUN curl -SL "https://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION-x64.msi" -o node.msi && \
    Start-Process -Wait -FilePath "msiexec.exe" -ArgumentList "/i", "node.msi", "/quiet" && \
    Remove-Item -Force node.msi && \
    npm install -g npm@$NPM_VERSION && \
    npm cache clean --force

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install npm dependencies
RUN npm install

# Copy the rest of the backend application files to the working directory
COPY . .

# Expose port 5000 
EXPOSE 5000

# Start the backend server
CMD ["node", "server.js"]
