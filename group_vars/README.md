# Variables

You cant customize some deployment setting by simply editing the variables files:

## SSL/HTTPS

### Using an existing SSL certificate

1. Create a directory named `ssl` inside `roles/nginx/files` (_ignored in git_)
2. Copy your `.crt` and `.key` files inside `roles/nginx/files/ssl/`.
3. Make sure your files name (before the `.crt` or `.key`) matches with the ***server_name*** variable, i.e:

 If you set your ***server_name*** variable to `inventivehack.com` you must have to files called `inventivehack.com.crt` and `inventivehack.com.key`

4. You're all set 😀

### Self signed SSL:

Make sure you have change this inside [group_vars/all/ssl.yml](all/ssl.yml):

* server_name
* ssl_on: **true**
* ssl_self_signed: **true**
* ssl_country
* ssl_state
* ssl_location
* ssl_organization
* ssl_organization_unit

### Variables

Can be found in [group_vars/all/ssl.yml](all/ssl.yml):

|    Variable     |     Default     |                      Description                      |
| --------------- |:---------------:| -----------------------------------------------------:|
|server_name|`example.com`|Domain name used for the site|
|ssl_on |`true`|Used to determine whether to use or not SSL: *Possible values*: `true`, `false`|
|ssl_self_signed |`true`|If `true`, will automatically create a self signed certificate: *Possible values*: `true`, `false`|
|ssl_certificates_path |`/etc/nginx/ssl`|Directory used to store the SSL certificates: **IMPORTANT:** Do not append any slash (`/`) at the end|
|ssl_expiration_days |`365`|Number of day for the certificate to expire|
|ssl_country |`MX`|Country used in the **CSR**|
|ssl_state |`Mexico City`|State used in the **CSR**|
|ssl_location |`Mexico City`|Location used in the **CSR**|
|ssl_organization |`Inventive`|Organization name used in the **CSR**|
|ssl_organization_unit |`""`|Organization unit name used in the **CSR**|

## PostgreSQL

Can be found in [group_vars/all/db.yml](all/db.yml):

|   Variable   |   Default   |             Description             |
| ------------ |:-----------:| -----------------------------------:|
|   db_host    | `127.0.0.1` |          PostgeSQL DB host          |
|   db_user    |   `ghost`   | PostgeSQL user that will own the DB |
| db_password  |   `admin`   |      PostgeSQL user's password      |
|   db_name    |   `blog`    |          PostgeSQL DB name          |


## Ghost

Can be found in [group_vars/all/ghost.yml](all/ghost.yml):

|    Variable     |     Default     |                      Description                      |
| --------------- |:---------------:| -----------------------------------------------------:|
|   ghost_post    |     `8080`      |   Local port in which ghost server will be running    |
|   ghost_path    |  `/srv/ghost/`  |  Directory used for downloading and installing ghost  |
|   ghost_group   |     `ghost`     |                Name of the Linux group                |
|    ghost_user   |     `ghost`     |                Name of the Linux user                 |
|    mail_user    |      `""`       |               Mailgun user credentials                |
|  mail_password  |      `""`       |             Mailgun password credentials              |