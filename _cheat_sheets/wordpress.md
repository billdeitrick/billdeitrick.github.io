---
description: Wordpress tips, tricks and procedures.
---

## Read-Only WordPress Site

Sometimes it's helpful to make a WordPress site read-only while making upgrades or changes. This can be helpful for blue/green deployments or other scenarios. The easiest way to do this is revoke all privileges for the database user, and grant them only "select" privileges for the desired time. Then, once ready, privileges can be reverted so the site becomes writable again. It is recommended to throw up a site-wide banner or similar so visitors can see an explanation for why form submissions and other write actions will err out during this time.

### Make site read only:

(assuming "wordpress" is the WordPress database user and the name of the database is also "wordpress")

```sql
revoke all privileges, grant option from 'wordpress'@'localhost';
grant select on wordpress.* to 'wordpress'@'localhost';
flush privileges;
```

### Make site writeable again

```sql
revoke all privileges, grant option from 'wordpress'@'localhost';
grant all on wordpress.* to 'wordpress'@'localhost';
flush privileges;
```
