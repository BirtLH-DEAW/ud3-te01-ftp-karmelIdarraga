# Dockerfile para el contenedor 1 FTP anonymous
# Crea una nueva imagen a partir de ubuntu, verisón latest

FROM ubuntu:latest

# Da información sobre la imagen que estamos creando
# Podemos usar la \ para encadenar todos los valores
LABEL \
	authors="kidarraga" \
	version="1.0" \
	description="Ubuntu + proftpd" \
	creationDate="17-12-2024"

# Ejecutamos diferentes comandos
# Debemos encadenarlos en un mismo RUN mediante la \

RUN \
	apt-get update \
	&& apt-get -y install proftpd 

# Podemos copiar todos los ficheros que ncesitemos
COPY index.html /srv/ftp/
COPY css_index /srv/ftp/css_index/
COPY proftpd.conf /etc/proftpd/

# Indica el puerto que utiliza la imagen
# para que lo mapeemos al crear el contenedor
EXPOSE 21
EXPOSE 50000-50030

# Si los ficheros están en la nube o comprimidos en un TAR
# podemos usar ADD
# ADD URL o TAR dir_destino

# Variables de entorno para la imagen
# ENV MYSQL_ROOT_PASSWORD root