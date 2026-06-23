FROM mysql:5.7

ENV MYSQL_ROOT_PASSWORD=root
ENV MYSQL_DATABASE=covid19
ENV MYSQL_USER=user
ENV MYSQL_PASSWORD=password

COPY covid19.sql /docker-entrypoint-initdb.d/
