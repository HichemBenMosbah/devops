#Use an official Node.js runtime as the base image
FROM node:18

# Set the working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the app source code
COPY . .

# Expose the backend port
EXPOSE 3001

# Start the backend application
CMD ["npm", "start"]

