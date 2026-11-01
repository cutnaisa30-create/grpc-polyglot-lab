FROM node:24-alpine

WORKDIR /app

# Salin konfigurasi dependensi
COPY node-client/package.json node-client/package-lock.json ./

# Instal hanya dependensi production
RUN npm ci --omit=dev --ignore-scripts \
    && npm cache clean --force

# Salin file proto dari folder utama
COPY user.proto ../user.proto

# Salin kode client
COPY node-client/client.js ./client.js

CMD ["node", "client.js"]

FROM node:24-alpine

WORKDIR /app

# Salin konfigurasi dependensi
COPY node-client/package.json node-client/package-lock.json ./

# Instal hanya dependensi production
RUN npm ci --omit=dev --ignore-scripts \
    && npm cache clean --force

# Salin file proto dari folder utama
COPY user.proto ../user.proto

# Salin kode client
COPY node-client/client.js ./client.js

CMD ["node", "client.js"]
