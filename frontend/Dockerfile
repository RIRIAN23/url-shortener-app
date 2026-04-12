# Stage 1: Build
FROM oven/bun:1 AS builder
WORKDIR /app

COPY package.json bun.lock ./
RUN bun install --frozen-lockfile

COPY . .
RUN bun run build


# Stage 2: Runtime
FROM nginx:alpine

# build output
COPY --from=builder /app/dist /usr/share/nginx/html

# custom nginx config
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
