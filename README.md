# mattys-malfunction-menders
Matty's Pathfinder Group Project

For those using Digital Ocean (DO) - nginx light, please follow the below steps to enable assistance Server Side Includes (SSI)

Run below commands in your DO console:
`cat etc/nginx`
`cd sites-enabled`
`cat default`

Add `ssi on;` to the `location` section in the `default` file to enable SSI for the root path `/`


```
location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                ssi on;
                try_files $uri $uri/ =404;
        }
```

`cd /` to access top-level directory.

`/etc/nginx/sites-enabled` this is the directory where backend server configuration lives.

`/var/www/html` this is the directory where frontend assets live.
