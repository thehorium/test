FROM debian
RUN apt update && apt upgrade -y && apt install nano curl gnupg2 ca-certificates lsb-release net-tools -y \
&& echo "deb http://nginx.org/packages/debian buster nginx" | tee /etc/apt/sources.list.d/nginx.list \
&& curl -fsSL https://nginx.org/keys/nginx_signing.key | apt-key add - \
&& apt update \
&&  apt install nginx -y \
&& mkdir /etc/nginx/www
COPY . index.htm /etc/nginx/www/
COPY . nginx.conf /etc/nginx/
RUN chown -R www-data:www-data /etc/nginx
RUN rm -rf /etc/nginx/conf.d
WORKDIR /etc/nginx/www
EXPOSE 5001
CMD ["nginx", "-g", "daemon off;"]
