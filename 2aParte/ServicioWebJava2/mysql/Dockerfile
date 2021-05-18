#############################################
# Fichero Dockerfile para Imagen Base mysql #
#############################################

FROM mysql:5.7

# Modificamos el fichero my.conf para que el formato sea compatible
# volumenes Windows y MAC
RUN echo [mysqld] >> /etc/mysql/my.cnf
RUN echo "innodb_use_native_aio=0" >> /etc/mysql/my.cnf

EXPOSE 3306