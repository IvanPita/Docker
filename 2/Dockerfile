#Partimos de una imagen Ubuntu
FROM ubuntu:20.04

#Linea para que no pregunte al hacer la instalacion
ENV DEBIAN_FRONTEND=noninteractive

#Actualizamos los repositorios e instalamos Apache, PHP, el módulo que los conecta y Git
RUN apt-get update && apt-get install -y \
    apache2 \
    php \
    libapache2-mod-php \
    git

#Limpiamos el directorio por defecto de Apache para que no haya conflictos
RUN rm -rf /var/www/html/*

#Clonamos una aplicacion y movemos los archivos al directorio de Apache
RUN git clone https://github.com/eshwar-sai-sai/Rock-Paper-Scissors.git /tmp/app && \
    cp -r /tmp/app/* /var/www/html/ && \
    rm -rf /tmp/app

#Exponemos el puerto 80
EXPOSE 80

#Añadimos esta linea para que no se apague la máquina y se quede ejecutando apache
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
