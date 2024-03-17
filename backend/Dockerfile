# Use the official Windows NanoServer image as base
FROM mcr.microsoft.com/windows/nanoserver:1709

# Download the package we want and unzip it to our destination
RUN curl.exe -o node.zip https://nodejs.org/dist/v9.2.0/node-v9.2.0-win-x64.zip && \
  mkdir "C:\\Program Files\\node" && \
  tar.exe -xf node.zip -C "C:\\Program Files\\node" --strip-components=1

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
