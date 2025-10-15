# ===============================
# 🏗️  Stage 1 — Build Angular app
# ===============================
FROM node:18 AS build

# Set working directory inside container
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the Angular source code
COPY . .

# Build the Angular app for production
RUN npm run build --prod


# ===============================
# 🚀 Stage 2 — Serve with Nginx
# ===============================
FROM nginx:alpine

# Copy built Angular files from Stage 1
COPY --from=build /app/dist /usr/share/nginx/html

# Expose default Nginx port
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]

