#****The first stage****
# Use the official Node.js image as the base image
FROM node as build
# Set the working directory inside the container
WORKDIR /app
# Copy package.json and package-lock.json to the working directory
COPY package*.json ./
# Install the dependencies
RUN npm install
# Copy the rest of the application files to the working directory
COPY . .
# Build the React application
RUN npm run build


#****The second stage****
# Use the official Nginx image to serve the built application
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html

