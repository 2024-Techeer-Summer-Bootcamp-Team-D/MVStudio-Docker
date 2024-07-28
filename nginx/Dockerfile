# nginx/Dockerfile
FROM nginx:latest

RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d
COPY app /etc/nginx/conf.d/app

CMD [ "nginx", "-g", "daemon off;" ]