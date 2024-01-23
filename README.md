# mattys-malfunction-menders
Matty's Pathfinder Group Project

For those using Digital Ocean (DO) - nginx light, please follow the below steps to enable Server Side Includes (SSI)

Run below commands in your DO console:

`cd /etc/nginx`

`cd sites-enabled`

`cat default` to view the file

`nano default` to edit the file (to enable SSI)


Add `ssi on;` to the `location` section in the `default` file to enable SSI for the root path `/`


```
location / {
                ssi on;

                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                try_files $uri $uri/ =404;
        }
```

Run `systemctl restart nginx` to restart Nginx server since the server configuration was changed

---


`cd /` to access top-level directory.

`/etc/nginx/sites-enabled` this is the directory where backend server configuration lives.

`/var/www/html` this is the directory where frontend assets live.

---

To copy the assets from the cloned Github repo, `cd` into the directory.
Example: `cd mattys-malfunction-menders/Matty\'s\ Malfunction\ Menders\ Website/`

The above `cd` command is run in DO Console which prefers to escape special characters and spaces.

Then run `cp -R * /var/www/html/` this will copy over the files from the Github repo.

---

To take the server down, in the DO console type `systemctl stop nginx`
We should see the default 503 "Backend unavailalbe" error page from the Fastly layer.

To bring the server back up, in the DO console type `systemctl start nginx`
Do a hard refresh on the browser, if all goes well, you should see the content from index.html file
