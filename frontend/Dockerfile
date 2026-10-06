FROM node:18
WORKDIR /app

COPY package.json package.json
COPY package-lock.json package-lock.json

# Настраиваем npm на использование зеркала и увеличиваем таймауты
RUN npm config set registry https://registry.npmmirror.com \
    && npm config set fetch-retries 5 \
    && npm config set fetch-retry-mintimeout 20000 \
    && npm config set fetch-retry-maxtimeout 120000

RUN npm install

COPY . .
RUN npm run build

CMD ["npx", "-y", "http-server", "-p", "8000", "/app/build"]