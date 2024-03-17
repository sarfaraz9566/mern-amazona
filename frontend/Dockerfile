# Use the official Windows Server Core image as the base image
FROM mcr.microsoft.com/windows/servercore:ltsc2019

# Set the working directory inside the container
WORKDIR /app/frontend

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install npm dependencies
RUN npm install

# Copy the rest of the frontend application files to the working directory
COPY . .

# Expose port 3000 (adjust as needed)
EXPOSE 3000

# Start the frontend development server
CMD ["npm", "start"]
