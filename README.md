# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Зозуля Максим`

### Задание 1  

Установите Zabbix Server с веб-интерфейсом.

*Приложите скриншот авторизации в админке. Приложите текст использованных команд в GitHub.*  

### Ответ:  
![pic1](https://github.com/shtitz1985/9-02-hw/blob/main/1.png)  

```
wget https://repo.zabbix.com/zabbix/6.4/debian/pool/main/z/zabbix-release/zabbix-release_6.4-1+debian11_all.deb
dpkg -i zabbix-release_6.4-1+debian11_all.deb
apt update
apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
apt install postgresql
sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
nano /etc/zabbix/zabbix_server.conf (строка DBPassword)
systemctl restart zabbix-server zabbix-agent apache2
systemctl enable zabbix-server zabbix-agent apache2
```  

---

### Задание 2  

Установите Zabbix Agent на два хоста.

*Приложите скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу. Приложите скриншот лога zabbix agent, где видно, что он работает с сервером. Приложите скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные. Приложите текст использованных команд в GitHub.*  

### Ответ:  

![pic2](https://github.com/shtitz1985/9-02-hw/blob/main/2.png)  
![pic3](https://github.com/shtitz1985/9-02-hw/blob/main/3.png)  
![pic4](https://github.com/shtitz1985/9-02-hw/blob/main/4.png)  
![pic5](https://github.com/shtitz1985/9-02-hw/blob/main/5.png)  
![pic6](https://github.com/shtitz1985/9-02-hw/blob/main/6.png)  

```
apt install zabbix-agent
sed -i 's/Server=127.0.0.1/Server=51.250.20.37'/g' /etc/zabbix/zabbix_server.conf
systemctl start zabbix-agent
systemctl enable zabbix-agent

```  

---  

