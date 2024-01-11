# piku-django-scale

The repository to support my presentation at [Scale 21x](https://www.socallinuxexpo.org/scale/21x) for [Piku](https://github.com/piku/piku)

# Installation
- Build a VM

- Install PIKU onto the VM using [Piku-Bootstrap](https://github.com/piku/piku-bootstrap)  

```
curl https://piku.github.io/get | sh
sudo ./piku-bootstrap install piku.yml
```

-  Back on the client, Grab the repo, setup PIPENV and add piku user to remote GIT repo
```
git clone https://github.com/jfmatth/piku-django-scale.git
cd piku-django-scale
pipenv shell
pipenv update
git remote add piku piku@server:appname
```

# Test local version
Django app  
```
python manage.py migrate
python manage.py runserver
```
browse to http://127.0.0.1:8000 to test


# Push code to piku and GIT hooks
```
git push piku
```

You'll need to use a git feature called hooks that rebuilds the ```requirements.txt``` file on a commit, since Pipenv doesn't create one automatically.

In the file .git/pre-commit, add the following code
```
#!/bin/bash

# Generate requirements.txt from Pipfile
pipenv sync
pipenv requirements > requirements.txt

# Add requirements.txt to the commit
git add requirements.txt
```


## Configure environment
```
piku run -- python manage.py migrate --no-input
piku config:set NGINX_SERVER_NAME=<your FQDN of site and server>
```

## Test FQDN
Browse to the FQDN

## PIKU commands

Display and follow logs
```
piku logs
```

Scale app +1 (add another UWSGI instance)
```
piku ps:scale wsgi=2
```

Shell into instance for local commands
```
piku shell
```

Run command on server
```
piku run
```


# Presentation

I just want to push code.pdf
