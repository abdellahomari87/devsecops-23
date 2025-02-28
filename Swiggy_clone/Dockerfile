# Stage 1: Build the React front-end
FROM node:18 AS frontend
WORKDIR /app
COPY package*.json ./
RUN npm install --legacy-peer-deps
COPY public/ ./public/
COPY src/ ./src/
RUN npm run build

# Stage 2: Setup Express server with the built front-end
FROM node:18
RUN apt-get update && apt-get upgrade -y && apt-get autoremove -y && apt-get clean

WORKDIR /app
COPY --from=frontend /app/build ./build  # Copie le dossier build du front-end
COPY server.js .
COPY package*.json ./
RUN npm install express  # Installe uniquement express pour le back-end
RUN npm install --legacy-peer-deps  # Installe les dépendances nécessaires pour le serveur

EXPOSE 3000
CMD ["node", "server.js"]
