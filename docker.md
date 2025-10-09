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
* This is interesting in general: What if you want to run a graphical application from within a docker container and you're using docker on WSL? `docker run -it -v /tmp/.X11-unix:/tmp/.X11-unix -v /mnt/wslg:/mnt/wslg \
    -e DISPLAY=$DISPLAY -e WAYLAND_DISPLAY=$WAYLAND_DISPLAY \
    -e XDG_RUNTIME_DIR=$XDG_RUNTIME_DIR -e PULSE_SERVER=$PULSE_SERVER -it yourimage:tag /bin/bash`
  This works if you are using WSLg,some docs here: https://github.com/microsoft/wslg
* Passing build secret through env vars, for example if you want to clone stuff from a git remote repo:
  * Dockerfile: `RUN --mount=type=secret,id=token DEPLOYTOKEN=$(cat /run/secrets/token) && git clone https://youruname:${DEPLOYTOKEN}@gitlab.com/whatever/you/want/coolrepo.git`
  * Build command (of course set the env var in your shell beforehands): `docker build  --secret id=token,env=DEPLOYTOKEN --file Dockerfile . -t coolimage:bestversion`
