SELF SIGNED
1.Generate RSA private key
openssl genrsa -out coderkaye.key 2048
> coderkaye.key (private key)
2.Extract public key from the key pair
openssl rsa -in coderkaye.key -pubout -out coderkaye_publickey.key
> coderkaye.key (public key)
3. Create CSR
openssl req -new -key coderkaye.key -out coderkaye.csr
> coderkaye.csr (certificate signing request)
4. Verify the CSR before passing to CA
openssl req -text -in coderkaye.csr -noout -verify
5. Sign the certificate
openssl x509 -in coderkaye.csr -out coderkaye.crt -req -signkey coderkaye.key -days 365
> This creates the certificate
