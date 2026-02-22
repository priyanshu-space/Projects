FROM node:18-alpine

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm ci --only=production

COPY . .

USER node

# Expose the application port
EXPOSE 3000

# Start the application
CMD [ "node", "index.js" ]
