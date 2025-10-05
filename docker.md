## Security tips

* [Owasp docker security checklist](https://cheatsheetseries.owasp.org/cheatsheets/Docker_Security_Cheat_Sheet.html
* [Running docker in rootless mode](https://docs.docker.com/engine/security/rootless/)
* 

## Scanning(OSS stuff)

* [Quay's Clair, scans images for known vulnerabilities](https://quay.github.io/clair/howto/deployment.html)
* [Threatmapper, mantained by deepfence. Threat scanner agent, can run on vm](https://threatmapper.org/)
* [Trivy scanner](https://github.com/aquasecurity/trivy) 
* [TruffleHog is the most powerful secrets Discovery, Classification, Validation, and Analysis tool](https://github.com/trufflesecurity/trufflehog)
* [Secretscanner for another well, secret scanner - same guys as threatmapper](https://github.com/deepfence/SecretScanne)
* [docker-bench-security](https://github.com/docker/docker-bench-security)

## Commands

* Connect to shell of running container: `docker exec -it idofcontainer /bin/bash`
* Special Docker DNS record for connecting from within a container to something running on the host: `host.docker.internal`
