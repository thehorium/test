FROM debian
RUN apt update && apt upgrade -y && apt install nano curl gnupg2 ca-certificates lsb-release net-tools -y \
&& echo "deb http://nginx.org/packages/debian buster nginx" | tee /etc/apt/sources.list.d/nginx.list \
&& curl -fsSL https://nginx.org/keys/nginx_signing.key | apt-key add - \
&& apt update \
&&  apt install nginx -y \
&& mkdir /etc/nginx/ssl
COPY nginx.conf /etc/nginx/
COPY ./ssl/cert.pem ./ssl/cert.key /etc/nginx/ssl/
RUN chown -R www-data:www-data /etc/nginx
RUN rm -rf /etc/nginx/conf.d
EXPOSE 443
CMD ["nginx", "-g", "daemon off;"]
