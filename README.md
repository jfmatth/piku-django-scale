# piku-django-scale

The repository to support my presentation at [Scale 21x](https://www.socallinuxexpo.org/scale/21x) for [Piku](https://github.com/piku/piku)

# Installation
```
git clone https://github.com/jfmatth/piku-django-scale.git
pipenv shell
git remote add piku piku@server:appname

git push piku
piku config:add NGINX_SERVER_NAME=<fqdn>

```

## Configure environment
```
piku config:set NGINX_SERVER_NAME=<your FQDN of site and server>
```

## PIKU commands
```
piku logs

piku restart

piku scale

piku shell

piku run
```

# Presentation

I just want to push code.pdf
