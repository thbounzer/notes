## Pki cookbook

* Generate csr and key (reasonable params) : `openssl req -out your.fqdn.csr -new -newkey rsa:2048 -nodes -sha256 -keyout your.fqdn.key`;

* (SUGGESTED) CN are going to be deprecated, so create a config file (ssl.conf) and set always Subject Alternatives Names:

    [ req ]
    default_bits       = 2048
    distinguished_name = req_distinguished_name
    req_extensions     = req_ext
    [ req_distinguished_name ]
    countryName                 = Country Name (2 letter code)
    stateOrProvinceName         = State or Province Name (full name)
    localityName               = Locality Name (eg, city)
    organizationName           = Organization Name (eg, company)
    commonName                 = Common Name (e.g. server FQDN or YOUR name)
    [ req_ext ]
    subjectAltName = @alt_names
    [alt_names]
    DNS.1   = dns.name.one
    DNS.2   = dns.name.two
    
    Then create CSR and key: `openssl req -out your.fqdn.csr -new -newkey rsa:2048 -nodes -sha256 -keyout your.fqdn.key -config ssl.conf`


* Submit to CA owners and ask for signing;

* *(optional)* Check the generated csr: `openssl req -text -noout -verify -in CSR.csr`
 

* Depending on your situation, you will need to create a bundle crt that contains root CA crt, (optional: intermediate CA crt) and you signed crt.
    * If yes:
        * Concat files with cat: `cat your.fqdn.crt intermediate.crt root.crt > your.fqdn.bundle.crt`

* If a root or intermediate crt is in binary form, could be that the crt format is DER
    * Verify is DER: `openssl x509 -in root.crt -inform der -text -noout`
    * To convert a DER to PEM crt: `openssl x509 -in root.crt -inform der -outform pem -out root.crt.pem `
    * Verify is PEM: `openssl x509 -in root.crt.pem -text -noout`

* Post-install verification:
    * Use s_client: `openssl s_client -connect your.fqdn:443`
    * Maybe you are using SNI: `openssl s_client -connect your.fqdn:443 -servername your.fqdn`

* Trust new certificates (CAs in theory) (debian)
    * Copy the certificate in pem format inside /usr/local/share/ca-certificates/
    * Certificate needs to HAVE crt extensions
    * run as root update-ca-certificates
    * profit


* Perhaps you want to verify if the key matches the certificate (for some arcane obscure reasons):
    * The modulus and the public exponent portions in the key and the Certificate must match. But since the public exponent is usually 65537 and it's bothering comparing long modulus you can use the following approach:
    * openssl x509 -noout -modulus -in server.crt | openssl md5
    * openssl rsa -noout -modulus -in server.key | openssl md5
    * Both hashes should match, of course

