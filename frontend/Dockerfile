# --- BUILD STAGE ---
FROM node:20 AS build
WORKDIR /app

# Copiar solo package.json (porque NO tienes package-lock.json)
COPY package.json ./
RUN npm install

# Copiar todo el frontend
COPY . .

# Construir Vite
RUN npm run build

# --- RUN STAGE ---
FROM nginx:alpine

COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]