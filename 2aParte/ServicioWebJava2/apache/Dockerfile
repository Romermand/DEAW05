####################################################################
# Fichero Dockerfile para Imagen Base Ubuntu 18.04 + Java + Apache #
####################################################################

# Creamos la imagen a partir de ubuntu versión 18.04
FROM ubuntu:18.04

# Damos información sobre la imagen que estamos creando
LABEL \
	version="1.0" \
	description="Ubuntu + Java" \
	creationDate="18-05-2021" \
	maintainer="David Romero <dromero@birt.eus>"

#Instalamos apache2 y 
#Java Open JDK alternativa libre
RUN apt-get -y update && apt-get -y upgrade \
	&& apt-get install -y apache2 \
    && apt-get -y install libapache2-mod-fcgid \
    && apt-get -y install openjdk-8-jdk 

#Borramos caché de paquetes apt y lista de paquetes descargada
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Copiamos fichero *.tar.gz
COPY target.tar.gz /tmp
RUN cd /tmp && tar -xzvf target.tar.gz

## Ejecutamos el archivo ServiciosWeb_mysql-0.0.1-SNAPSHOT.jar
RUN cd /tmp && java -jar ServiciosWeb_mysql-0.0.1-SNAPSHOT.jar

## Eliminar instaladores descargados
RUN cd /tmp && rm *.gz

#Exponemos puertos
EXPOSE 80

# Arrancamos el servidor apache una vez que se ha creado el contenedor
# No tenemos que acceder a él para ponerlo en marcha
CMD ["apachectl", "-D", "FOREGROUND"]
