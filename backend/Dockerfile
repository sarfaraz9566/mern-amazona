# Use the official Windows Server Core image as the base image
FROM mcr.microsoft.com/windows/servercore:ltsc2019

# Set the working directory inside the container
WORKDIR /app/backend

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
