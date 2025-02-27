## 1. Créer une Container Grafana

```bash
docker run -d --name=grafana -p 8080:3000 -v g_config:/etc/grafana -v g_data:/var/lib/grafana -v g_logs:/var/log/grafana grafana/grafana

```

## 2. Créer un container MySQL

```bash
docker run -d --name mysqldb -p 3306:3306 -v db_data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=Inspire123 mysql:latest

```

Connect to mysql:

```bash
mysql -u root -p -h 127.0.0.1

## provide the password: Inspire123

mysql> create database InspireDEV;
Query OK, 1 row affected (0.07 sec)

mysql> use InspireDEV
Database changed
mysql>

CREATE TABLE CloudEngineer ( eng_id INT NOT NULL PRIMARY KEY, first_name VARCHAR(40) NULL, last_name VARCHAR(40) NULL, role VARCHAR(40) NULL, created TIMESTAMP );


mysql> Show tables;
+----------------------+
| Tables_in_InspireDEV |
+----------------------+
| CloudEngineer        |
+----------------------+
1 row in set (0.03 sec)

```

```sql
INSERT INTO CloudEngineer (eng_id, first_name, last_name, role) VALUES (1,'Mohamed','B', 'Solutions Architect');

INSERT INTO CloudEngineer (eng_id, first_name, last_name, role) VALUES (2, 'Mamadou', 'D.', 'Kubernetes Engineer');

INSERT INTO CloudEngineer (eng_id, first_name, last_name, role) VALUES (3, 'Ben', 'B.', 'Solutions Architect');

INSERT INTO CloudEngineer (eng_id, first_name, last_name, role) VALUES (4, 'Elon', 'Musk', 'CEO');
```

```sql
CREATE USER 'grafana' IDENTIFIED BY 'grafana';
GRANT SELECT ON InspireDEV.* TO 'grafana';
flush privileges;
```
