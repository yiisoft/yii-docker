# Install an application template

Enter the `php` container:

```bash
    composer create-project yiisoft/app /app
```

Open in your browser: `http://127.0.0.1:8000`

When running Apache you need a configuration like the following to use `enablePrettyUrl` in `.htaccess` in your public `public` folder:

```apache
    RewriteEngine on
    # If a directory or a file exists, use it directly
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    # Otherwise forward it to index.php
    RewriteRule . index.php
```
