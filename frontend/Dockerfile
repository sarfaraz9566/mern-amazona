# frontend/Dockerfile
FROM mcr.microsoft.com/windows/nanoserver:1809 AS build

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM mcr.microsoft.com/windows/nanoserver:1809
WORKDIR /app
COPY --from=build /app/build ./build
EXPOSE 3000
CMD ["npm", "start"]
