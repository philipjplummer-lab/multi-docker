FROM node:lts-alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . . 
RUN npm run build

FROM nginx
EXPOSE 3000
COPY /wsl.localhost/Ubuntu/home/philip/complex/nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html

#base image
#FROM node:lts-alpine 
#WORKDIR '/app'
#COPY ./package.json ./
#RUN npm install
#COPY . . 
#CMD ["npm","run","start"]