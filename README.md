# grafana-prometheus-mysql
Coletando metricas do mysql, importando no prometheus e visualizando no grafana dashboard


# Crie um usuário no banco de dados mysql para ter acesso as metricas

CREATE USER 'exporter'@'localhost' IDENTIFIED BY 'password' WITH MAX_USER_CONNECTIONS 3;
GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'exporter'@'localhost';

# Baixar e configurar o msyql_exporter

Dicas: https://grafana.com/oss/prometheus/exporters/mysql-exporter/?tab=installation

# Baixar o mysql_exporter
wget https://github.com/prometheus/mysqld_exporter/releases/download/v0.12.1/mysqld_exporter-0.12.1.linux-amd64.tar.gz

tar xvfz mysqld_exporter-*.*-amd64.tar.gz
cd mysqld_exporter-*.*-amd64

# Criar um usuario no banco de mysql
CREATE USER 'exporter'@'localhost' IDENTIFIED BY 'enter_password_here' WITH MAX_USER_CONNECTIONS 3;
GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'exporter'@'localhost';

# set a seguinte variavel de ambiente
export DATA_SOURCE_NAME='exporter:enter_password_here@(mysql_hostname:3306)/'

# Execute o comando abaixo
./mysqld_exporter

# Crie um arquivo chamado my.cnf em um diretorio e configure assim:

[client]

user=exporter

password=password-exporter

host=mysql-server


