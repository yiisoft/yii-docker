# Instalando um modelo de aplicativo

Entre no contêiner `php`:

```bash
    composer create-project yiisoft/app /app
```

Abra no seu navegador `http://127.0.0.1:8000`

Ao executar o Apache você precisa de uma configuração como a seguinte para usar `enablePrettyUrl` em `.htaccess` em sua pasta pública `public`:

```html
     RewriteEngine ativado
     # Se existir um diretório ou arquivo, use-o diretamente
     ReescreverCond %{REQUEST_FILENAME} !-f
     ReescreverCond %{REQUEST_FILENAME} !-d
     # Caso contrário, encaminhe para index.php
     RewriteRule . index.php
```
