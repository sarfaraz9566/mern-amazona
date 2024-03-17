# backend/Dockerfile
FROM mcr.microsoft.com/windows/nanoserver:1809

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .

EXPOSE 5000
CMD ["node", "index.js"]
