# Use Node.js as base image
FROM node:latest

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json to container
COPY /my-app/package*.json ./

# Install dependencies
RUN npm install

# Copy all files from the current directory to the container
COPY ./my-app/ .

# Expose port 3000
EXPOSE 3000

# Command to run the React app
CMD ["npm", "start"]
