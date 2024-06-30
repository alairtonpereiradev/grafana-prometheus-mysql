# grafana-prometheus-mysql
Coletando metricas do mysql, importando no prometheus e visualizando no grafana dashboard


# Crie um usuário no banco de dados mysql para ter acesso as metricas

CREATE USER 'exporter'@'localhost' IDENTIFIED BY 'password' WITH MAX_USER_CONNECTIONS 3;
GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'exporter'@'localhost';

# Baixar e configurar o msyql_exporter
# Clone o repositorio

git clone https://github.com/prometheus/mysqld_exporter

# Crie um arquivo chamado my.cnf em um diretorio e configure assim:

[client]

user=exporter

password=password-exporter

host=mysql-server

Entre na pasta mysql_exporter e execute o arquivo

./mysqld_exporter /diretorio/my.cnf
