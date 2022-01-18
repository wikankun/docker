# Prerequisites

Link to the full tutorial:
https://www.digitalocean.com/community/tutorials/how-to-use-traefik-v2-as-a-reverse-proxy-for-docker-containers-on-ubuntu-20-04

# Setup Traefik Username and Password

```
sudo apt-get install apache2-utils
```

Generate the password with htpasswd. Substitute secure_password with the password you'd like to use for the Traefik admin user:

```
htpasswd -nb admin <secure_password>
```

The output from the program will look like this:

```
admin:$apr1$ruca84Hq$mbjdMZBAG.KWn7vfN/SNK/
```

# Setup traefik network and files

```
docker network create web
```

```
touch acme.json
```

```
chmod 600 acme.json
```

# Add these lines to your docker-compose settings

```
labels:
- traefik.http.routers.adminer.rule=Host(`sub_domain.your_domain`)
- traefik.http.routers.adminer.tls=true
- traefik.http.routers.adminer.tls.certresolver=lets-encrypt
- traefik.port=8080
networks:
- web
```

and

```
networks:
  web:
    external: true
```