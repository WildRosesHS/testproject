FROM debian


# накатывает на базовый образ nginx и php-fpm
RUN apt-get -y update && apt-get -y install apt-transport-https
RUN apt-get -y update && apt-get -y install nginx
RUN apt-get -y update && apt-get -y install php-fpm
# загружает необходимую библиотеку для работы php с postgres
RUN apt-get -y update && apt-get -y install php-pgsql

# создает дирректорию для загрузки сайта
RUN mkdir -p /sites/test.project.com

# сертификат для сервера nginx
# RUN mkdir /etc/nginx/ssl
# COPY privateKey.key /etc/nginx/ssl/privateKey.key
# COPY certificate.crt /etc/nginx/ssl/certificate.crt

# копирует файлы сайта в созданную папку
COPY index.php /sites/test.project.com/index.php

# копирует кастомный файл конфигурации nginx, php-fpm и заменяет стандартные; копирует скрипт для запуска сервисов
COPY nginx.conf /etc/nginx/nginx.conf
COPY www.conf /etc/php/8.2/fpm/pool.d/www.conf
COPY script.sh script.sh


# указывает порт, на котором будет доступен контейнер извне
# EXPOSE 80/tcp

# запускает скрипт для сервисов
CMD ./script.sh