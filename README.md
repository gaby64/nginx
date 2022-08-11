Based on https://github.com/sftcd/nginx/tree/ECH-experimental, this fork implements Encrypted Client Hello with BoringSSL.

```
bssl generate-ech -out-ech-config-list echconfiglist.data -out-ech-config main.ech -out-private-key main.key -public-name frontend.example.com -config-id 0
```

place the *.ech and *.key in the folder of your choice that you configured in your nginx.conf with

```
http {
  ssl_echkeydir echkeydir;
}
```

place the base64 encoded echconfiglist in your https dns entry ech attribute
```
base64 -w 0 echconfiglist.data
```

tested to work on Chrome Dev 106 with experiment flags #use-dns-https-svcb-alpn, #encrypted-client-hello, #dns-https-svcb and DNS over HTTPS enabled.



# nginx
An official read-only mirror of http://hg.nginx.org/nginx/ which is updated hourly. Pull requests on GitHub cannot be accepted and will be automatically closed. The proper way to submit changes to nginx is via the nginx development mailing list, see http://nginx.org/en/docs/contributing_changes.html
