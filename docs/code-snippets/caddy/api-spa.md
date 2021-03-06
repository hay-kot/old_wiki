# SPA and API

```
{
  auto_https off
}

:80 {
  @proxied path /api/* /docs /openapi.json

  root * /app/dist
  encode gzip
  uri strip_suffix /
  
  handle @proxied {
    reverse_proxy http://127.0.0.1:9000 
  }

  handle {
    try_files {path}.html {path} /
    file_server 
  }

}
```