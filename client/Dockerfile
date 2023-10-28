FROM node:20-alpine AS builder

WORKDIR /app
COPY ./package.json ./
RUN npm install
COPY . .

CMD ["npm", "run", "build"]

FROM nginx
EXPOSE 3000
COPY --from=builder /app/build /usr/share/nginx/html
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf