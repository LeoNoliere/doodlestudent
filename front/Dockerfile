FROM node:20 AS build

WORKDIR /doodlestudent

COPY . .

EXPOSE 4200 8080

RUN npm install

RUN npm run build --prod

FROM nginx

COPY --from=build /doodlestudent/dist/tlcfront/ /usr/share/nginx/html

RUN rm /etc/nginx/conf.d/default.conf
