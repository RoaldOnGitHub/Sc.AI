FROM php:8.1-fpm-alpine
WORKDIR /var/www/html
COPY . /var/www/html

# Устанавливаем нужные пакеты и настройки (msmtp и т.д.)
RUN apk update && apk add msmtp
RUN echo "sendmail_path = '/usr/bin/msmtp -C /etc/msmtprc -t'" > /usr/local/etc/php/conf.d/sendmail.ini

# Прочие настройки msmtp
COPY msmtprc /etc/msmtprc
RUN chown 82:82 /etc/msmtprc && chmod 600 /etc/msmtprc
RUN touch /var/log/msmtp.log && chmod 666 /var/log/msmtp.log

EXPOSE 9000
CMD ["php-fpm"]


