FROM debian

RUN echo "deb http://mirror.docker.ru/debian/ bullseye main non-free" > /etc/apt/sources.list.d/docker.list && \
    apt update && \
    apt upgrade -y && \
    apt install -y nginx && \
    apt clean && \
    rm -rf /var/www/* && \
    mkdir -p /var/www/company.com/img
    
COPY index.html /var/www/company.com/

ADD content_img.tar /var/www/company.com/img

RUN chmod -R 754 /var/www/company.com && \
    useradd alexander && \
    groupadd slobodchikov && \
    usermod -a alexander -G slobodchikov && \
    chown -R alexander:slobodchikov /var/www/company.com && \
    sed -i 's/\/var\/www\/html/\/var\/www\/company.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data;/user alexander;/g' /etc/nginx/nginx.conf

