# multi step docker builder process
FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
# Expose port 3000 instead of the default port 80
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# Copy the app build files to the nginx html directory
COPY --from=builder /app/build /usr/share/nginx/html
