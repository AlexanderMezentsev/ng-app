# BUILD PHASE
FROM node:24-alpine AS builder

WORKDIR /usr/app
COPY package.json package-lock.json ./
RUN npm ci
COPY ./ ./

RUN npm run build

# RUN PHASE
FROM nginx:alpine
COPY --from=builder /usr/app/dist/webui/browser /usr/share/nginx/html