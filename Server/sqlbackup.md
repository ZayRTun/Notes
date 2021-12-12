**Home**
- [Home](../index.md)
---

# Server Sql Back and download

## Creating sql backup file with `mysqldump`
```bash
mysqldump -u root -p goldenland > /home/zayar/sqlbackup/goldenlandbackup.sql
```
## Copying the file from ther server to my laptop with `scp`
```bash
scp zayar@139.180.191.12:/home/zayar/sqlbackup/goldenlandbackup.sql ~/Downloads/glbackup.sql
```