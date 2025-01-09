FROM nginx:latest
COPY default.conf /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/nginx.conf
COPY ./staticfiles ./app/staticfiles
COPY ./dist ./app/dist
