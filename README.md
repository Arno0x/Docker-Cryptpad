### CryptPad is the zero knowledge realtime collaborative editor.
  
To start the image in background (daemon mode):

`docker run -d -p 3000:3000 arno0x0x/cryptpad-auto`
  
You can then browse to the main page using http://your_server_name:3000/
 
You might also want to use a volume to store the encrypted data outside of the container in order to make it persistent accross container recycling:

`docker run -d -p 3000:3000 -v /path/to/datastore:/cryptpad/datastore arno0x0x/cryptpad-auto`

Beware that by default the image is **not** reachable through HTTPS **which is not secure**. If you want (*and you do want it*) HTTPS, then when creating your container:
- Copy all SSL required files (*key, certificate and CA cert chain*) into the container - or - map a volume containing those files into your container (`-v /path/to_all_ssl_files:/path/to_files_in_container`)
- Modify the config.js to point to these file as described on the cryptpad container, basically:

```
privKeyAndCertFiles: [
   '/path/to/my_secret.key',
    '/path/to/my_public_cert.crt',
    '/path/to/my_certificate_authorities_cert_chain.ca'
]
```
