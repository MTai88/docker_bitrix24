FROM mysql:latest

COPY my.cnf /etc/mysql/conf.d/my.cnf
COPY init/ /docker-entrypoint-initdb.d/

CMD ["mysqld"]

EXPOSE 3306
