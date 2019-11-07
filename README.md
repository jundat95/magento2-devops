# DevOps for magento 2.3.x

*Docker Image to Magento 2.3.x local development in Mac, Linux and Windows*

## Nginx + PHP-FPM 7.2.x + MySQL 5.7 + PHPMyAdmin = <img src="magento.png" width="20" alt="magento">


## How to use

```bash

git clone https://github.com/jundat95/magento2-devops.git

Copy code Magento 2 to folder ./www

Change config mysql ./bin/env/db.env

```

### Run docker with magento fresh and create a new db (local)

```bash

Go to workspace

sudo sh ./bin/bash/install-default

```

### Run docker with project and exists db (local)

```bash

Copy file database to ./bin/db, file name example: dump.sql

Go to workspace

sudo sh ./bin/bash/install-local

```

### Run docker with project and exists db (server)

```bash

Copy file database to ./bin/db, file name example: dump.sql

Go to workspace

sudo sh ./bin/bash/install-prod

```
