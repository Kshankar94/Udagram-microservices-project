# Use NodeJS base image
FROM node:13
FROM beevelop/ionic AS ionic

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies by copying
# package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy app source
COPY . .

# ionic build
RUN ionic build

COPY . .


FROM nginx:alpine

COPY --from=ionic /usr/src/app/www /usr/share/nginx/html
