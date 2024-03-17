# Use a Windows Nano Server image as the base image
FROM mcr.microsoft.com/windows/nanoserver:1809 AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json (if present) to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of your application code to the working directory
COPY . .

# Build the React app
RUN npm run build

# Use a smaller, optimized image for production
FROM mcr.microsoft.com/windows/nanoserver:1809

# Set the working directory inside the container
WORKDIR /app

# Copy the built app from the builder stage
COPY --from=builder /app/build ./build

# Expose the port your app runs on
EXPOSE 3000

# Command to run your app
CMD ["cmd", "/S", "/C", "node", "build/index.js"]
