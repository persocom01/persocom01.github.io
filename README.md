# persocom01.github.io

Personal profile website.

## Optimization

Many professional websites leave out the .html extensions on links. To do this, you need to modify the .htaccess on the webserver by adding the following code:

```
RewriteEngine on
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ $1.html [L,QSA]
```

nginx servers have no .htaccess files, so the servers' .conf file have to be modified instead:

```
location / {
  if (!-e $request_filename){
    rewrite ^(.*)$ /$1.html break;
  }
}
```
