https://medium.com/@nh3500/how-to-create-self-assigned-ssl-for-local-docker-based-lamp-dev-environment-on-macos-sierra-ab606a27ba8a

# set local cert
https://donatstudios.com/Self-Signed-Certificate-On-macOS-Apache

```
openssl req -newkey rsa:2048 -x509 -nodes \
    -keyout localhost.key \
    -new \
    -out localhost.crt \
    -subj /CN=localhost \
    -reqexts SAN \
    -extensions SAN \
    -config <(cat /System/Library/OpenSSL/openssl.cnf \
        <(printf '[SAN]\nsubjectAltName=DNS:localhost')) \
    -sha256 \
    -days 3650
```

or mkcert
https://donatstudios.com/Local-Certificate-On-macOS-Apache