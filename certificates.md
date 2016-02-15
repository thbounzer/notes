## Pki cookbook

* Generate csr and key (reasonable params) : `openssl req -out your.fqdn.csr -new -newkey rsa:2048 -nodes -sha256 -keyout your.fqdn.key`;
* Submit to CA owners and ask for signing;

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
