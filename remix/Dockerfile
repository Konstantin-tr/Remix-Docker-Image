# Source image
FROM node:21-bullseye-slim as base
ENV NODE_ENV production

# Copy package.json and package-lock.json
FROM base as manifest
WORKDIR /remix
COPY package*.json ./

# Install the node modules
FROM manifest as packages
WORKDIR /remix
RUN npm ci --include=dev

# Prune all node modules you won't use in production
FROM packages as prod-packages
WORKDIR /remix
RUN npm prune --production

# Copy the source files
FROM packages as copy-source
WORKDIR /remix
COPY . .

# Build the project from the source files
FROM copy-source as build
WORKDIR /remix
RUN npm run build

# Copy build artifacts
FROM prod-packages as copy-build
COPY --from=build /remix/build /remix/build 
COPY --from=build /remix/public /remix/public

# Rune the project
FROM copy-build
WORKDIR /remix
EXPOSE 3000
CMD ["npm", "run", "start" ]