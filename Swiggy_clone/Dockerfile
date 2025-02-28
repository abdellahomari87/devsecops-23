FROM node:18
RUN apt-get update && apt-get upgrade -y && apt-get autoremove -y && apt-get clean

# Build React front-end
WORKDIR /app/client
COPY client/package*.json ./
RUN npm install
COPY client/ .
RUN npm run build

# Setup Express server
WORKDIR /app/server
COPY server/package*.json ./
RUN npm install
COPY server/ .
RUN cp -r /app/client/build /app/server/public  # Remplace COPY --from=0

EXPOSE 3000
CMD ["node", "app.js"]
