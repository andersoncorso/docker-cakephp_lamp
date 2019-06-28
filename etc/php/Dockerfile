# Imagem base PHP Apache 7.3.6
FROM php:7.3.6-apache 

# Variáveis env
ENV DEPS="libicu-dev libpq-dev libmcrypt-dev mysql-client zip unzip zlib1g-dev libmcrypt-dev" \
    APP_HOME="/var/www/html/app"
    
# Instalando dependencias do sistema e habilitando modulos PHP
RUN apt-get update && apt-get install -y ${DEPS} \
    && rm -r /var/lib/apt/lists/* \
    && docker-php-ext-install \
      intl \
      mbstring \
      pcntl \
      pdo_mysql \
      opcache \
      && pecl install mcrypt-1.0.2

# Instalando composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin/ --filename=composer

# Mudando o UID e GID do apache para o Docker
RUN usermod -u 1000 www-data && groupmod -g 1000 www-data \
# Mudando o web_root para cakephp  Apache /var/www/html/webroot 
    && sed -i -e "s/html/html\/app\/webroot/g" /etc/apache2/sites-enabled/000-default.conf \
# Habilitando modulo rewrite
    && a2enmod rewrite


# Cópia da aplicação para o container
COPY . $APP_HOME

# Mudança do usuário dono da aplicação
RUN chown -R www-data:www-data $APP_HOME