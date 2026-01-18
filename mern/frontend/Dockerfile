#I used Node.js 20 LTS with an Alpine base image to ensure long-term stability, security updates, and minimal container size for efficient deployment
FROM node:20-alpine

# Set working directory inside container - 
#WORKDIR sets the default directory inside the container so all subsequent commands execute in a predictable and isolated location, improving readability and avoiding path-related issues
WORKDIR /app 


#Copies package.json from your local project into the container’s WORKDIR (/app)
COPY package.json .
#I copy package.json first to leverage Docker’s layer caching so dependency installation is only re-run when dependencies change, not on every code change.

#Installs all dependencies listed in package.json inside the container.Copies everything else (source code, routes, controllers, etc.) into the container.
RUN npm install

#Copies all frontend source files from your local system into the container’s WORKDIR (usually /app)
COPY . .

#Documents that the container listens on port 5173.
# 📌 Vite dev server runs on 5173 by default.
EXPOSE 5173

# Starts the Vite development server when the container runs
CMD ["npm", "run", "dev"]
# I expose port 5173 because Vite runs on that port by default, and I use npm run dev to start the development server inside the container.

