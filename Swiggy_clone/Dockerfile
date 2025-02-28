FROM node:18
RUN apt-get update && apt-get upgrade -y && apt-get autoremove -y && apt-get clean

# Build React front-end
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY public/ ./public/
COPY src/ ./src/
RUN npm run build

# Setup Express server
WORKDIR /app
COPY server.js .
RUN npm install express  # Installe express si ce n'est pas déjà fait

EXPOSE 3000
CMD ["node", "server.js"]
