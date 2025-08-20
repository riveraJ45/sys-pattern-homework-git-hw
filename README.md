Ривера Александр Андреевич Домашнее задание к занятию «Система мониторинга Zabbix»



Я решил все это дело сделать я вндекс облаке развернул там 2 вируталки на debian и поставил на 1 машину сервер котоырй монитор себя и 2 хост, вроде все получилось) 

### Задание 1
# Установка PostgreSQL
sudo apt install postgresql postgresql-contrib -y
sudo systemctl enable postgresql
sudo systemctl start postgresql

# Создание пользователя и базы
sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix

# wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_latest_6.0+debian11_all.deb
# dpkg -i zabbix-release_latest_6.0+debian11_all.deb
# apt update

# Установка Zabbix Server, Frontend, Agent
sudo apt install zabbix-server-pgsql zabbix-frontend-php php-pgsql zabbix-apache-conf zabbix-agent -y

# Импорт схемы базы данных
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

# Настройка конфига Zabbix
sudo nano /etc/zabbix/zabbix_server.conf
# DBPassword=zabbix

# Запуск служб
sudo systemctl restart zabbix-server zabbix-agent apache2
sudo systemctl enable zabbix-server zabbix-agent apache2



 Скриншоты

https://github.com/riveraJ45/sys-pattern-homework-git-hw/blob/ebe600ebf12c2653800bac58be2df955ad9bfd52/1.jpg


### Задание 2

я писать не стал все команды, они одинаковые, просто я помто поменял конфиг через эти команды чтобы он видел сервер и правильное имя хоста написал
# Настройка конфига
sudo nano /etc/zabbix/zabbix_agentd.conf
# Изменено:
Server=10.0.1.3,158.160.45.45
Hostname=zabbixhosts





Скриншоты

https://github.com/riveraJ45/sys-pattern-homework-git-hw/blob/ebe600ebf12c2653800bac58be2df955ad9bfd52/2.1.jpg
https://github.com/riveraJ45/sys-pattern-homework-git-hw/blob/ebe600ebf12c2653800bac58be2df955ad9bfd52/2.2.jpg
https://github.com/riveraJ45/sys-pattern-homework-git-hw/blob/ebe600ebf12c2653800bac58be2df955ad9bfd52/2.3.jpg