# Домашнее задание к занятию 9.2 «Zabbix. Часть 1» - Баранов Сергей


# Задание 1

### Установите Zabbix Server с веб-интерфейсом.
###### Приложите скриншот авторизации в админке.
![monitoring](https://github.com/12sergey12/9.2_zabbix.-.1/blob/main/images/9-1-000.png)

#####Приложите текст использованных команд в GitHub.
* ip a
* sudo apt update
* sudo apt upgrade
* sudo apt install postgresql
* wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4%2Bdebian11_all.deb
* ls
* dpkg -i zabbix-release_6.0-4+debian11_all.deb
* export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
* dpkg -i zabbix-release_6.0-4+debian11_all.deb
* ls -la /etc/apt/sources.list.d/
* ls -la /etc/apt/sources.list.d/zabbix.list
* cat /etc/apt/sources.list.d/zabbix.list
* apt update
* sudo apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts nano -y # zabbix-agent
* cat /etc/postgresql
* cat /etc/passwd
* postgres
* su postgres
* su - postgres -c 'psql --command "CREATE USER zabbix WITH PASSWORD '\'123456789\'';"'
* su - postgres -c 'psql --command "CREATE DATABASE zabbix OWNER zabbix;"'
* zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
* sudo nano /etc/zabbix/zabbix_server.conf
* sudo nano /etc/zabbix/zabbix_server.conf
* sed -i 's/# DBPassword=/DBPassword=123456789/g' /etc/zabbix/zabbix_server.conf
* nano /etc/zabbix/zabbix_server.conf
* ip a
* sudo systemctl restart zabbix-server apache2 # zabbix-agent
* sudo systemctl enable zabbix-server apache2 # zabbix-agent
* apt install zabbix-agent
* systemctl status zabbix-agent.service


# Задание 2

### Установите Zabbix Agent на два хоста.

###### Приложите скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу.
######  Приложите скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.
![monitoring](https://github.com/12sergey12/9.2_zabbix.-.1/blob/main/images/9-2-2%20config-hosts.png)
###### Приложите скриншот лога zabbix agent, где видно, что он работает с сервером.
![monitoring](https://github.com/12sergey12/9.2_zabbix.-.1/blob/main/images/9-2-2-agent-log-vm1.png)
![monitoring](https://github.com/12sergey12/9.2_zabbix.-.1/blob/main/images/9-2-2-agent-log-vm2.png)
![monitoring](https://github.com/12sergey12/9.2_zabbix.-.1/blob/main/images/9-2-3-latest%20data%20%D0%BE%D0%B1%D1%89%D0%B5%D0%B5.png)
###### Приложите текст использованных команд в GitHub.
* sudo apt update
* wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4%2Bdebian11_all.deb
* dpkg -i zabbix-release_6.0-4+debian11_all.deb
* export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
* dpkg -i zabbix-release_6.0-4+debian11_all.deb
* sudo apt install zabbix-agent -y
* sudo systemctl restart zabbix-agent
* sudo systemctl enable zabbix-agent
* find / -name zabbix_agentd.log
* tail -f /var/log/zabbix/zabbix_agentd.log
* systemctl status zabbix-agent.service
* nano /etc/zabbix/zabbix_agentd.conf
* sed -i 's/Server=127.0.0.1/Server=192.168.0.22/g' /etc/zabbix/zabbix_agentd.conf
* nano /etc/zabbix/zabbix_agentd.conf
* systemctl restart zabbix-agent.service
* systemctl status zabbix-agent.service


# Задание 3*

### Установите Zabbix Agent на Windows (компьютер) и подключите его к серверу Zabbix.

###### Приложите скриншот раздела Latest Data, где видно свободное место на диске C:

