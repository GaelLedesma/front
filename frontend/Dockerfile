# --- BUILD STAGE ---
FROM node:20 AS build
WORKDIR /app

# Copiar package.json y lockfile
COPY package.json package-lock.json ./
RUN npm install --production=false

# Copiar el resto del código
COPY . .

# Construir el proyecto
RUN npm run build

# --- RUN STAGE ---
FROM nginx:alpine

# Copiar archivos generados por Vite
COPY --from=build /app/dist /usr/share/nginx/html

# Puerto (Railway lo ignora pero no pasa nada)
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]