# Important-commands

## 🚀 Starting the Server

To start a simple HTTP server in the current directory, use the following command:

```
python3 -m http.server
```
If the above command is not working:

```
python -m http.server
```


## 🔐 Reset Odoo Admin Credentials in PostgreSQL

To reset the Odoo admin username and password directly via PostgreSQL, run the following steps:

```bash
sudo -u postgres psql -d db_name
```
Then inside the PostgreSQL shell, execute:

```
UPDATE res_users SET password = 'admin' WHERE id = 2;
```
```
UPDATE res_users SET login = 'admin' WHERE id = 2;
```

⚠️ Note: The correct table name is res_users (plural), not res_user.



## 📦 Download Database from Live Server

1️⃣ Create Database Backup on Server

SSH into your server and run:
```
cd /tmp
sudo -u postgres pg_dump db_name > backup.sql
```

For compressed backup (recommended):
```
cd /tmp
sudo -u postgres pg_dump db_name | gzip > backup.sql.gz
```

2️⃣ Download Backup to Local Machine

Run this command on your local system:
```
scp root@your_server_ip:/tmp/backup.sql .
```

For compressed file:
```
scp root@your_server_ip:/tmp/backup.sql.gz .
```
