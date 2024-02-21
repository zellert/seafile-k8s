# seafile-k8s
Seafile CE behind Traefik.

Adjust "seahub_settings.py" within provisioned PVC:

```
+ SERVICE_URL = "https://PUBLIC_FQDN/"
+ CSRF_TRUSTED_ORIGINS = ["https://PUBLIC_FQDN"]
+ FILE_SERVER_ROOT = "https://PUBLIC_FQDN/seafhttp"
```

Bind to memcached via pod loopback ip:

```
CACHES = {
    'default': {
        ...
        'LOCATION': '127.0.0.1:11211',
...
}
```

Don't forget to redeploy pod after changes.
