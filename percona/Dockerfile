FROM --platform=linux/amd64 percona:8.0

COPY my.cnf /etc/mysql/conf.d/my.cnf
COPY init/ /docker-entrypoint-initdb.d/

USER root

CMD ["mysqld"]

EXPOSE 3306
