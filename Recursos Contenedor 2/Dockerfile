# Dockerfile para el contenedor 1 FTP anonymous
# Crea una nueva imagen a partir de ubuntu, verisón latest

FROM ubuntu:latest

# Da información sobre la imagen que estamos creando
# Podemos usar la \ para encadenar todos los valores
LABEL \
	authors="kidarraga" \
	version="1.0" \
	description="Ubuntu + protpd + openssl" \
	creationDate="17-12-2024"

# Ejecutamos diferentes comandos
# Debemos encadenarlos en un mismo RUN mediante la \

RUN \
apt-get update \
&& apt-get -y install proftpd \
&& apt-get -y install openssl \
&& apt-get install  -y  proftpd-mod-crypto \
&& useradd deaw -m -d /srv/deaw  --password "$(openssl passwd -1 "deaw")" --shell /bin/false \
&& openssl genpkey -algorithm RSA  -out /etc/ssl/private/kidarraga-ftpserver.key -pkeyopt rsa_keygen_bits:4096 \
&& openssl req -new -key /etc/ssl/private/kidarraga-ftpserver.key -x509 -days 365 -out /etc/ssl/certs/kidarraga-ftpserver.crt  -subj "/C=EU/ST=Bizkaia/L=Mungia/O=Karmel Idarraga/CN=www.kidarraga-birt.eus/emailAddress=kidarraga@birt.eus"
    

# Podemos copiar todos los ficheros que ncesitemos
COPY DefaultRoot_comandos.txt FTP_comandos.txt FTPanonimo_comandos.txt /srv/deaw/
COPY proftpd /etc/proftpd/

# Indica el puerto que utiliza la imagen
# para que lo mapeemos al crear el contenedor
EXPOSE 21
EXPOSE 50000-50030

# Si los ficheros están en la nube o comprimidos en un TAR
# podemos usar ADD
# ADD URL o TAR dir_destino

# Variables de entorno para la imagen
# ENV MYSQL_ROOT_PASSWORD root