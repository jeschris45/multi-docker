FROM node:alpine as builder
WORKDIR './app'
COPY ./package.json .
RUN npm install
COPY . . 
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx.default.conf /app/build/usr/share/nginx/html
COPY --from=builder /app/build /app/build/usr/share/nginx/html