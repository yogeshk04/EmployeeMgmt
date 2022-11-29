# Stage 1: Compile and Build angular codebase

# Use official node iamge as the base image
FROM node:latest as build
# Set the working directory
WORKDIR /usr/local/app
# Add the source code to app
COPY ./ /usr/local/app
# Install all the dependencies
RUN npm install
#RUN npm i -g json-server
#RUN json-server --watch db.json
# Generate the build of the application
RUN npm run build

# Stage 2: Serve app with ngixn server 

# User official nginx image as the base image
FROM nginx:latest
# Copy the build output to replace teh default nginx contents
COPY --from=build /usr/local/app/dist/employeemgmt /usr/share/nginx/html
# Expose port
EXPOSE 80