#Use an official Node.js runtime as the base image
FROM node:18

# Set the working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the app source code
COPY . .

# Build the frontend application
RUN npm run build

# Install serve to serve the build
RUN npm install -g serve

# Expose the frontend port
EXPOSE 3000

# Start the frontend application
CMD ["serve", "-s", "build"]

