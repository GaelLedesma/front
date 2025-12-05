# Etapa 1 — Construcción con Node + npm
FROM node:20 AS build

WORKDIR /app

# Copiar archivos de dependencias
COPY package.json package-lock.json ./

# Instalar dependencias con npm
RUN npm install

# Copiar el resto del proyecto
COPY . .

# Construir el proyecto
RUN npm run build

# Etapa 2 — Servir estático con nginx
FROM nginx:stable

COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]