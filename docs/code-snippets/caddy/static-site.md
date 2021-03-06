# Static Site Config

```
{
  auto_https off # Disable HTTPS
}

:80 {
  root * /srv
  encode gzip
  uri strip_suffix / # Optional

  handle {
    try_files {path} {path}/ /index.html
    file_server 
  }

}
```