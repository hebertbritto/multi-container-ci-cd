FROM node:latest AS buildnode

WORKDIR '/app'

COPY package.json .

RUN npm install
#RUN npm install react-scripts -g
COPY ./ ./
#VOLUME node_modules .:/app
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=buildnode /app/build /usr/share/nginx/html