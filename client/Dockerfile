FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . . 
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# COPY --from=bulider ./nginx/default.conf /etc/nginx/conf.d/default.conf ***this doesn't not solve the issue***
COPY --from=builder /app/build /usr/share/nginx
