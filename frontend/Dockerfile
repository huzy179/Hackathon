FROM node:20-alpine

ARG NEXT_PUBLIC_API_URL=https://hackathon-production-a4a7.up.railway.app

ENV NEXT_TELEMETRY_DISABLED=1 \
    HOSTNAME=0.0.0.0 \
    NEXT_PUBLIC_API_URL=${NEXT_PUBLIC_API_URL} \
    PORT=3000

WORKDIR /app

COPY package*.json ./
RUN npm ci --include=dev

COPY . .

RUN npm run build

ENV NODE_ENV=production

EXPOSE 3000

CMD ["sh", "-c", "npm run start -- --hostname 0.0.0.0 --port ${PORT}"]
